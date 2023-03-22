# GenericNetworker :hammer_and_wrench:

A Generic iOS network handler leveraging URLSession

## Elevate Your iOS App's Networking Capabilities with Our Network Handler

Looking for a reliable and efficient solution for network communication in your iOS applications? Look no further than our iOS network handler. Our powerful tool leverages the capabilities of URLSession to provide a flexible and easy-to-use interface for managing and executing network requests within your app.

## Key Features

- Generic design suitable for a wide range of use cases
- Built specifically for iOS for optimal performance and reliability
- Integrates seamlessly with URLSession framework
- Streamlines your app's network communication for a seamless user experience

## Getting Started

To get started with our network handler, simply install the package and import it into your project. You can then begin using the tool to manage and execute network requests within your app.

### Follow the steps below to add the package/dependency to your project :fire:

&#9830; Open your Xcode project.

&#9830; Go to File > Swift Packages > Add Package Dependency. This will open a window to add a new package.

&#9830; In the "Add Package Dependency" window, you can enter the URL https://github.com/Sidney-Okine/GenericNetworker.git

&#9830; After you've entered the package information, click "Next".

&#9830; In the next screen, you can select the version of the package you want to use. You can also specify a branch, tag, or commit to use.

&#9830; Select the option "Up to the next major version" to keep your package up to date.

&#9830; In the next screen, you can choose the targets for the package. You can select one or more targets to add the package to.

&#9830; After you've selected the targets, click "Finish". Xcode will then download and add the package to your project.

### Graphical Illustration below :point_down:
- 1.
![image](https://user-images.githubusercontent.com/85578453/226907155-56b2b738-ca12-497a-b9ec-b85fb7b90c81.png)

- 2.
![image](https://user-images.githubusercontent.com/85578453/226910240-edcf06bf-401e-42e9-aa50-cb63cafac44f.png)

- 3.
![image](https://user-images.githubusercontent.com/85578453/226910478-af0a5f92-1f71-4e32-8d14-c7fd5389f7f4.png)

- 4.
![image](https://user-images.githubusercontent.com/85578453/226911539-2241031a-b77d-4dbc-8061-61eb3b092fc7.png)

- 5.
![image](https://user-images.githubusercontent.com/85578453/226912772-86ae4216-d7a9-48b0-9b02-2a7722ebf51f.png)
Done :heavy_check_mark:

&#9830; After you've added the package to your project, you can import the package in your Swift code using the import statement. For example, import my package like so:

```swift
  import GenericNetworker
```

## Examples
Here is a sample use case for my network handler:

A simple example of a Network Call to the [Jokes API](https://v2.jokeapi.dev/).

- 1. First define your Codable structs, for both response and request ( but in our case we'll only require a response struct )
```swift
// Response struct
// For the purposes of this demo, I have defined the entire structure. 👍🏾

struct JokesModel : Codable {
    let error : Bool?
    let category : String?
    let type : String?
    let joke : String?
    let flags : JokeFlags
    let id : Int?
    let safe : Bool?
    let lang : String
}

struct JokeFlags : Codable {
    let nsfw : Bool
    let religious : Bool
    let political : Bool
    let racist : Bool
    let sexist : Bool
    let explicit : Bool
}
```
- 2. Making the actual call :smile:

```swift
 Requester.shared.makeRequest(to: "https://v2.jokeapi.dev/joke", urlEndPoint: "/Programming", httpMethod: .GET, headers: httpHeaders(), expecting: JokesModel.self){result,error in
                           if error == nil {
//  I prefer only the joke in the response as I don't really know what I'll do with the rest 😅
//   You might as well call the entire struct like so; print(result)
                                        print(result?.joke as! String)
                                        }
                                         else {
                                             print(error?.localizedDescription)
                                         }
                           
                       }

```

The code above is a function call to a method called makeRequest that is defined in an object called Requester. The makeRequest method takes several arguments:

+ to (your baseUrl) : A string that specifies the URL to which the request is being made.
+ urlEndPoint : Another string that specifies the endpoint of the URL.
+ httpMethod: An enumeration type that specifies the HTTP method being used (e.g. GET, POST, PATCH etc.).
+ customBody: An optional argument that specifies the HTTP request body (if any).
+ headers: An optional dictionary that specifies HTTP headers to be included in the request(if there are changes to the basic three i.e Content-Type,Accept,Authorization(if any)).
+ additionalHttpHeaders: Another optional dictionary that specifies additional HTTP headers to be included in the request.
+ expecting: A type that is both Decodable and Encodable thus Codable.
+ completion: A closure that takes two arguments, a Codable object and an Error object. This closure is called when the request is complete

- My response in the console 

```console
Two C strings walk into a bar.
The bartender asks "What can I get ya?"
The first string says "I'll have a gin and tonic."
The second string thinks for a minute, then says "I'll take a tequila sunriseJF()#$JF(#)$(@J#()$@#())!*FNIN!OBN134ufh1ui34hf9813f8h8384h981h3984h5F!##@"
The first string apologizes, "You'll have to excuse my friend, he's not null-terminated."

```
The joke wasn't what I was hoping for :roll_eyes: but I guess it's funny so permit me to laugh :rofl:

Feel free to hit me up :call_me_hand:

Made with :heart:	by Sidney Okine
