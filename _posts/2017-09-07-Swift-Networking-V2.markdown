---
layout:     post
title:      "Swift Networking V2"
subtitle:   "URLSession, JSONParse, manipulating data"
date:       2017-08-16 10:55:55 AM
author:     "Rob"
---

# Getting Started

OK, I guess I underestimated exactly how much code would be required to actually properly design an app.

Even more so, you need to learn structs, how to break down the data into it's own constants, use the helper functions, detect errors, get inside the dicitonary of stored values, and learn to display the vlaues, check for status codes. 

# Tools 

Get POST MAN (On the App Store) NOW! It makes handling API requests that much easier. 

# Data Model

### Let's make it easier and follow the DRY principle. 

In the below example, we begin by setting up our data with a Struct, it is much more easily accessible and makes things a little bit faster. 

You can find more information as to why Structs are used in this example here: https://stackoverflow.com/questions/24232799/why-choose-struct-over-class/24232845

It mentions that structs are more preferred for storing simple values, that you will copy. Classes are meant to be a fallback. 

I'm just going to go with what they said on this one:

```
Struct Constants {


    Struct Flickr { 
        // Lets define our Constants here.
        
        // Using the Flickr Example from Udacity
        
        static let APIScheme = "https"
        static let APIHost = "api.flickr.com"
        static let APIPath = "/services/reset"
        
        // Create a bounding box at the lon/lat
        static let SearchBBoxHalfWidth = 1.0
        static let SearchBBoxHalfHeight = 1.0
        
        
        // Searching lat / longitude. 
        // This gives us accurate coordinates, -180, 180, -90, 90 
        // 90 degrees one way, and 180 degrees the other.
        static let SearchLatRange = (-90, 90.0)
        static let SearchLonRange = (-180.0, 180.0)         
    }
    
    Struct ParameterKeys {
        // setup the API parameters to save time on reusing.
        
        // (Update later) why do we use static let? (Because it needs to be public?)
        // You can find all of the parameters on Flickr's API page.
        
        static let Method = "method"
        static let APIKey = "api_key"
        static let GalleryID = "gallery_id"
        static let Extras = "extras"
        static let Format = "format"
        static let NoJSONCallback = "nojsoncallback"
        static let SafeSearch = "safe_search"
        static let Text = "text"
        static let BoundingBox = "bbox"
        static let Page = "page"
    }
    
    Struct ParameterValues { 
        static let SearchMethod = "flickr.photos.search"
        static let APIKey = "346082cd47e728b2d7a42bf4c945d5f0"
        static let ResponseFormat = "json"
        static let DisableJSONCallback = "1" /* 1 means "yes" */
        static let GalleryPhotosMethod = "flickr.galleries.getPhotos"
        static let GalleryID = "5704-72157622566655097"
        static let MediumURL = "url_m"
        static let UseSafeSearch = "1"
    }
    
    struct ResponseKey {
        static let Status = "stat"
        static let Photos = "photos"
        static let Photo = "photo"
        static let Title = "title"
        static let MediumURL = "url_m"
        static let Pages = "pages"
        static let Total = "total"
    }
    
    // MARK: Flickr Response Values
    struct FlickrResponseValues {
        static let OKStatus = "ok"
    }
    
    // FIX: As of Swift 2.2, using strings for selectors has been deprecated. Instead, #selector(methodName) should be used.  
    /*
    // MARK: Selectors
    
    // Convert this to work with latest Swift version. (Setup a shortcut for keyboard will show / hide, however there is a much better way (Through Extensions))
    struct Selectors {
        static let KeyboardWillShow: Selector = "keyboardWillShow:"
        static let KeyboardWillHide: Selector = "keyboardWillHide:"
        static let KeyboardDidShow: Selector = "keyboardDidShow:"
        static let KeyboardDidHide: Selector = "keyboardDidHide:"
    }
    */
}
```

This is almost a lot of code, but it's pretty simple. We store the values so we don't have to continue to type them over and over again. In my previous post, we use these values and call the methods along with the dictionary values so that we can get the desired result. Which is the whatever matches with the text in the text box. 

We also want to match this up with the text (lat, lon) inside of the textbox as well, but never use them at the same time. Another part of the construction of the app is also that the exact same code is called on both ```@IBActions``` which is pretty damn annoying. 

So I'll have the learn how we can turn that into one network request at some point. Not sure but it is probable, just ask Google. 

# Verifying errors

When you make an API call, theres a high chance if your values aren't properly configured that you will receive error response codes. For instance, let's say you have a dictionary value like so:

``` 
let methodParamters = { 
    Constants.Flickr.Method : Constants.Flickr.SearchMethod 
}
```

Here you see, we call our method, and value against each part. This requires a pretty good understanding of the web link / API (I would say it is best that you check out the link in the API as well as what is in your browser when viewing a photo on Flickr). This will alllow you to analyze and breakdown the web link into it's own parts. It's how we ended up with the SearchMethod Constant. 

Of course, all websites take different parameters, so I say, experiment. Use Post Man as this is going to save you so much time and headache when dealing with APIs.

We typically receive a response code when we make a request, handling this or "catching" this response code from the API request will allow us some flexibility in dealing with unexpected results. 

A simple example is as so: 

```
if let statusCode = 200 { 
    // Do some really good things 
} else { 
    print the localizedDescription   
}
```

Doing this we check if we have received a 200 (which means OK or Success). If we otherwise get a different message, print us the result. 

This lets us successfully grab data but also if there was an error we can further analyze our API request to make sure the keys and values were set properly. 

We can continue to do this for most if not all status codes. In swift this was also updated to instead use ```guard let``` instead of if let. I have to refresh on why and I'll keep you updated. 

# The Rest is History

So there you go, a bunch of explanation to the original post. It was extremely frustrating to go through this, wait till I write about the JSON. Also, since I'm here – download the chrome extension "JSON Viewer". You can thank me later. 

Regards,

Rob

