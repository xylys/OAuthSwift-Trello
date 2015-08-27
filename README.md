## OAuthSwift+Trello

Swift based OAuth library for iOS and OSX.

### Support OAuth1.0

Trello

### Installation

* Drag OAuthSwift-Trello to your project in the Project Navigator.
* Copy Files

### Setting URL Schemes

![Image](Assets/URLSchemes.png "Image")

### Examples

```swift
// AppDelegate
func application(application: UIApplication, openURL url: NSURL, sourceApplication: String?, annotation: AnyObject?) -> Bool {
    if (url.host == "oauth-callback") {
        OAuth1Swift.handleOpenURL(url)
    }

    return true
}

// In your networking class or wherever you need to get the oauth token
//
// Get your Trello api key and secret at: https://trello.com/1/appKey/generate

let oauthswift = OAuth1Swift(
    consumerKey:    "", // Your Trello api key
    consumerSecret: "", // Your Trello api secret
    requestTokenUrl: "https://trello.com/1/OAuthGetRequestToken",
    authorizeUrl:    "https://trello.com/1/OAuthAuthorizeToken",
    accessTokenUrl:  "https://trello.com/1/OAuthGetAccessToken",
    appName: "",  // The name of your application
    scope: "", // The permissions you want trello to give you: "read" or "read,write"
    expiration: "" // How long your token will work: "1day" or "30days" or "never"
)

// Then call:

oauthswift.authorizeWithCallbackURL(NSURL(string: "oauth-swift://oauth-callback/trello")!, success: { (credential, response) -> Void in

    println(credential.oauth_token)
    println(credential.oauth_token_secret)

}) { (error) -> Void in

    println("error")

}

```

## Thanks

Thanks to Dongri for making the original OAuthSwift library
https://github.com/dongri/OAuthSwift

## License

OAuthSwift+Trello is available under the MIT license. See the LICENSE file for more info.
