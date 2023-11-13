# swift-模型与Data互转

## Model转Data

``` swift

func convertModelToData(model: Model) -> Data? {
	let encoder = JSONEncoder()
	do {
		let data = try encoder.encode(model)
		return data
	} catch {
		print("模型转换Data失败")
		return nil
	}
}

```

## Data转Model

``` swift

func convertDataToModel(data: Data) -> Model? {
	let decoder = JSONDecoder()
	do {
		let model = try decoder.decode(Model.self, from: data)
		return model
	} catch {
		print("Data转模型失败")
		return nil
	}
}

```