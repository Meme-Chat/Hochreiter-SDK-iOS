# Hochreiter SDK iOS 

Welcome to the iOS Hochreiter SDK from MemeChat!

This SDK is designed to help developers easily integrate memes into their iOS applications. With just a few lines of code, your users will be able see and share hilarious memes with their friends and followers.

## Getting Started:

To use the iOS Hochreiter SDK in your application, there are 2 options.Simply download the [xcframwork](www.google.com) file and add it to your project. Other option is Swift Package Manager.You can then import the SDK into your code and start using it right away.


## 🎉 Installation SPM(Swift Package Manager)

Here are the steps to add Hochreiter SDK via SPM (Swift Package Manager):

- Open your Xcode project and select your project file in the Project Navigator.
- Select the project’s target you want to add the SDK to.
- Select the "Swift Packages" tab in the project editor.
- Click the "+" button to add a new package.
- In the "Choose Package Repository" dialog, enter the URL of the SDK repository: https://github.com/Meme-Chat/Hochreiter-SDK-iOS.git.
- Click "Next" and select the version of the SDK you want to use.
- Click "Next" again and choose the target you want to add the SDK to.
- Click "Finish" to add the SDK to your project.

Alternatively, you can add the package directly in your Package.swift file by adding the following code:

```swift
dependencies: [
    .package(url: "https://github.com/Meme-Chat/Hochreiter-SDK-iOS.git", .upToNextMajor(from: "1.0.0"))
]
```
This code will add the latest version of the SDK that is compatible with version 1.0.0 or higher. You can customize the version to fit your needs.

That's it! You can now use the SDK in your project.




## 🚀 Usage

To use the SDK:

```swift
import Hochreiter
```

Then configure the SDK by calling the configure function in your AppDelegate :

```swift
HochreiterSDK.configure(uname: "your_username", pass: "your_password")

```

Following are the methods open for use:

1. [Get Categories](https://github.com/Meme-Chat/Hochreiter-SDK-iOS/blob/mian/README.md#gc)
2. [Categories based Memes](https://github.com/Meme-Chat/Hochreiter-SDK-iOS/blob/mian/README.md#cbm)
3. [Search Memes](https://github.com/Meme-Chat/Hochreiter-SDK-iOS/blob/mian/README.md#sm)
4. [Log Meme Shared Event](https://github.com/Meme-Chat/Hochreiter-SDK-iOS/blob/mian/README.md#lms)
5. [Log Meme Viewed Event](https://github.com/Meme-Chat/Hochreiter-SDK-iOS/blob/mian/README.md#lmv)


#### Get Categories <a name="gc"></a>

The fetchCatagories method in HochreiterSDK is used to retrieve a list of all the categories available for memes on the Hochreiter platform. Here's an example of how to use it:

```swift
import Hochreiter

HochreiterSDK.fetchCatagories { result in
    switch result {
    case .success(let categories):
        // Handle the list of categories
    case .failure(let error):
        // Handle the error
    }
}
```
 This completion handler returns a Result type that can either be .success with an array of `Hochreiter.Cats` objects or .failure with a `Hochreiter.HUNetworkError` error.

`Hochreiter.Cats` contains name and identity.


#### Categories based Memes <a name="cbm"></a>

The `HochreiterSDK.fetchCatagoriesMemes` method is used to fetch the memes under a particular category. Here's how to use it:

```swift
import Hochreiter

HochreiterSDK.fetchCatagoriesMemes(categoryId: "Hochreiter.Cats.identity", page: 1) { result in
    switch result {
    case .success(let memes):
        // Handle the list of memes
    case .failure(let error):
        // Handle the error
    }
}
```

Here category_Id is `Hochreiter.Cats.identity`


The completion handler receives a Result enum with either the fetched `Hochreiter.CatagoriesMemes` object or a Hochreiter.HUNetworkError error.

the CatagoriesMemes struct has the following properties:

- `memes: [MemeList]:` An array of MemeList objects that represent the memes in the category.

`MemeList:` contains mid , url, height and width.



#### Search Memes <a name="sm"></a>

The fetchMemesWith function is a part of the HochreiterSDK that allows you to fetch memes based on a given search term and a page number. The function takes two parameters:

```swift
import Hochreiter

HochreiterSDK.fetchMemesWith(searchTerm: "search_term", page: 1) { result in
    switch result {
    case .success(let memes):
        // Handle the list of memes
    case .failure(let error):
        // Handle the error
    }
}
```

`searchTerm:` A string that represents the search term for the memes that you want to fetch. This parameter is required.

The completion handler receives a Result enum with either the fetched `Hochreiter.[MemeList]` object or a Hochreiter.HUNetworkError error.

`MemeList:` contains mid , url, height and width.

#### Log Meme Shared Event <a name="lms"></a>
```swift
import Hochreiter

HochreiterSDK.logMemeShared(mid: mid)
```
#### Log Meme Viewed Event <a name="lmv"></a>
```swift
import Hochreiter


HochreiterSDK.logMemeViewed(mid: mid)
```



