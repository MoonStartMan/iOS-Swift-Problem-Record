# swift获取通讯录联系人信息

## 方法一

一、引入CotactsUI

``` swift

import ContactsUI

```

二、通过代理方法获取通讯录中联系人信息

``` swift

extension ViewController : CNContactPickerDelegate {
    func contactPicker(_ picker: CNContactPickerViewController, didSelect contact: CNContact) {
        // 1.获取用户的姓名
        // lastname --> familyName
        // firstname --> givenName
        let lastname = contact.familyName
        let firstname = contact.givenName
        print("姓名:\(firstname) \(lastname)")
        
        // 2.获取用户电话号码(ABMultivalue)
        let phones = contact.phoneNumbers
        for phone in phones {
            let phoneLabel = phone.label
            let phoneValue = phone.value.stringValue
            print("phoneLabel:\(phoneLabel). phoneValue:\(phoneValue)")
        }
    }
}

```

## 方法二

Contacts

获取用户授权

``` swift

func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
        //1.获取授权状态
        //CNContactStore 通讯录对象
        let status = CNContactStore.authorizationStatus(for: .contacts)
        
        //2.判断如果是未决定状态,则请求授权
        if status == .notDetermined {
            
            //创建通讯录对象
            let store = CNContactStore()
            
            //请求授权
            store.requestAccess(for: .contacts, completionHandler: { (isRight : Bool,error : Error?) in
                
                if isRight {
                    print("授权成功")
                } else {
                    print("授权失败")
                }
            })
            
        }
        
        
        
        return true
    }

```

获取联系人信息

``` swift

//1.获取授权状态
let status = CNContactStore.authorizationStatus(for: .contacts)

//2.判断当前授权状态
guard status == .authorized else { return }

//3.创建通讯录对象
let store = CNContactStore()
        
//4.从通讯录中获取所有联系人

//获取Fetch,并且指定之后要获取联系人中的什么属性
let keys = [CNContactFamilyNameKey, CNContactGivenNameKey, CNContactPhoneNumbersKey]
//创建请求对象   需要传入一个(keysToFetch: [CNKeyDescriptor]) 包含'CNKeyDescriptor'类型的数组
let request = CNContactFetchRequest(keysToFetch: keys as [CNKeyDescriptor])
//遍历所有联系人
//需要传入一个CNContactFetchRequest
do {
		try store.enumerateContacts(with: request, usingBlock: {(contact : CNContact, stop : UnsafeMutablePointer<ObjCBool>) -> Void in
      //1.获取姓名
      let lastName = contact.familyName
      let firstName = contact.givenName
      print("姓名 : \(lastName)\(firstName)")

      //2.获取电话号码
      let phoneNumbers = contact.phoneNumbers
      for phoneNumber in phoneNumbers
			{
        print(phoneNumber.label ?? "")
        print(phoneNumber.value.stringValue)
			}
		})
  } catch {
    print(error)
  }
}

```

## 授权部分

在Info.plist里面添加Key

```

Privacy - Contacts Usage Description

```