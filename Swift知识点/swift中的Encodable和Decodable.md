# swift中的Encodable和Decodable

## Encoding

将自定义类型实例转换为其他表示形式(例如JSON和pList)的过程称为编码或序列化。对于编码，自定义类型符合Encodable协议。

## Decoding

将诸如JSON或pList之类的表示形式的数据转换为自定义类型的实例的过程称为解码或反序列化。对于解码，自定义类型符合Decodable协议。

## Codable

为了支持编码和解码，自定义类型可以符合Codable协议，而后者同时符合Encodable和Decodable。

``` swift

typealias Codable = Encodable & Decodable

```

## 自动编码和解码

默认情况下，Swift Standard Library和Foundation Framework中的许多类型（如Int，String，Data，URL，Date等）都是可编码的。为了使任何自定义类型都自动成为可编码的，它应符合可编码协议，并且其所有存储的属性都应是可编码的。

``` swift

struct MovieDetail: Codable {
	var language: String?
	var genre: String?
	var releaseDate: String?
	var bannerImageUrl: String?
}

struct Movie: Codable {
	var movieID: Int?
	var name: String?
	var movieDetails: MovieDetail?
}

```

由于MovieDetail也符合Codable，因此Movie也可编码。 Swift集合类型（例如Array，Dictionary和Optional）只要包含Codable类型，就变为Codable。

## JSONEncoder 和 JSONDecoder

假设您的自定义类型是Codable，则可以使用JSONEncoder将您的类型编码为其他类型，例如Data，可以将其发送到服务器或保存到磁盘。

要以raw bytes (Data) 编码Movie

``` swift

let bannerUrl = "https://example.com"
let movieDetails = MovieDetails(language: "English", genre: "Action", releaseDate: "18-05-2018", bannerImageUrl: bannerUrl)
let movie = Movie(movieId: 2, name: "Deadpool 2", movieDetails: movieDetails)
let jsonEncoder = JSONEncoder()
let movieData = try jsonEncoder.encode(movie)

```

** 编码函数会抛出并且可能失败，这就是为什么需要使用try的原因。 **

在Xcode调试控制台中，打印movieDate仅显示原始字节数，我们将其转换为可读的JSON字符串。

``` swift

let jsonString = String(data: movieData, encoding: .utf8)
print(jsonString)

```

现在，要将这些数据转换回Movie类型的实例，您需要使用JSONDecoder。

``` swift

let jsonDecoder = JSONDecoder.init()
if let data = movieData {
    let movie = try jsonDecoder.decode(Movie.self, from: data)
}

```

## 使用Coding Keys

可编码类型定义符合CodingKey协议的嵌套枚举CodingKeys，其情况定义编码或解码时必须包括的属性。属性的名称应与自定义类型中相应属性的名称匹配。要在编码表示形式或解码类型中排除某些属性，只需在CodingKeys枚举中省略它们。

如果您想要在编码数据中使用与自定义类型不同的键名，或者您的自定义类型中的某些属性名称与JSON中的某些属性名称不同，则将CodingKeys枚举的原始值类型定义为String并使用case提供原始值。

``` swift

struct Movie: Codable {
   var movieId: Int?
   var name: String?
   var movieDetails: MovieDetail?

   enum CodingKeys: String, CodingKey {
      
       case movieId = "id"
       case name 
       case movieDetails    
   }
}

```

## 手动实现Encoding和Decoding

如果自定义类型的结构与JSON的结构不同，则可以自己实现自己的编码和解码逻辑。

``` swift

let movieDetails = MovieDetails(language: "English", genre: "Action", releaseDate: "18-05-2018", bannerImageUrl: bannerUrl)
let movie = Movie(movieId: 2, name: "Deadpool 2", movieDetails: movieDetails)

```

要使用以下结构将此电影对象编码为JSON

``` swift

{ "movieId": 2, "name": "Deadpool 2", "language": "English", "genre": "Action", "releaseDate": "18-05-2018", "bannerUrl": "https://www.imdb.com/title/tt5463162/mediaviewer/rm4291446016" }

```

在这里，我们可以在上面的JSON中看到电影详细信息不像电影中那样是嵌套结构，我们可以使用编码功能将电影对象手动编码为上面的表示形式。

``` swift

encode(to: Encoder)

```

让我们使用CodingKeys更新Movie结构，如下所示：

``` swift

struct Movie {
    var movieId: Int?
    var name: String?
    var movieDetails: MovieDetail?
    enum CodingKeys: String, CodingKey {
        
       case language
       case genre
       case releaseDate
       case bannerUrl 
    }
}

```

现在，我们实现Encodable并描述encode函数内部的编码逻辑。

在这里，我将Movie结构的符合性更改为Encodable，而不是Codable，以仅演示编码。如果只需要对自定义类型执行编码，则可以使用Encodable，仅解码可以使用Decodable，如果需要对自定义类型执行编码和解码，则可以使用Codable。

``` swift

extension Movie: Encodable {
  func encode(to encoder: Encoder) throws {
    var container = encoder.container(keyedBy: CodingKeys.self)
    try container.encode(movieId, forKey: .movieId)
    try container.encode(name, forKey: .name)
    try container.encode(movieDetails.language, forKey: .language)
    try container.encode(movieDetails.genre, forKey: .genre)
    try container.encode(movieDetails.releaseDate, forKey: .releaseDate)
    try container.encode(movieDetails.bannerImageUrl, forKey:  .bannerUrl)
  }
}

```

此处的container提供了对编码器存储空间的API，可通过key进行访问。

现在，如果您编码并打印JSON字符串，您将获得

``` swift

{ "movieId": 2, "name": "Deadpool 2", "language": "English", "genre": "Action", "releaseDate": "18-05-2018", "bannerUrl": "https://www.imdb.com/title/tt5463162/mediaviewer/rm4291446016" }

```

如果我们必须将此JSON字符串转换为Movie类型的实例，则可以通过实现以下必需的初始化程序来手动解码

``` swift

init(from decoder: Decoder)

```

现在，我们将一致性更改为Decodable，并描述init内部的解码逻辑（来自解码器：Decoder）。

``` swift

extension Movie: Decodable {
  init(from decoder: Decoder) throws {
       
     var container = try decoder.container(keyedBy: CodingKeys.self)
     movieId = try container.decode(Int.self, forKey: .movieId)
  
     name = try container.decode(String.self, forKey: .name)
     let language = try container.decode(String.self, forKey: .language)
     let genre = try container.decode(String.self, forKey: .genre)
     let releaseDate = try container.decode(String.self, forKey: .releaseDate)
     let bannerUrl = try container.decode(String.self, forKey: .bannerUrl)
     movieDetails =  MovieDetail(language: language, genre: genre, releaseDate: releaseDate, bannerImageUrl: bannerUrl)             
    }
}

```

## 处理错误

JSONDecoder和JSONEncoder对象都配备了适当的错误处理机制，并且在编码和解码失败时会引发错误，这些错误为开发人员提供了明确的反馈，告知他们代码中到底出了什么问题。

JSONDecoder抛出DecodingError，其中包含不同的错误情况，例如.dataCorrupted，.keyNotFound，.typeMismatch，.valueNotFound。类似地，JSONEncoder会引发EncodingError以及编码期间可能出现的各种错误情况。