---
layout:     post
title:      "Swift Networking"
subtitle:   "URLSession, JSONParse, manipulating data"
date:       2017-08-09 10:55:55 AM
author:     "Rob"
---

# Getting Started

In this tutorial I go about understanding networking, calling an API, and parsing the JSON data received from the web service. 

Once we have received and parsed the data, we want to manipulate this data and do awesome stuff with it. 

# Networking with Swift s

In Swift, the URLSession method is instantiated as a Singleton class. A Singleton class is a shared instance and can only be instantiated once. Once you've created an Instance of ``` URLSession.shared ``` you can begin utilizing the methods from within. 

# Setup 

We begin setting up our data by writing the following code in the example below. I will be using a very simple API web service provided by Sandip Bhagat. http://sandipbgt.com/theastrologer/ we start by building the URL. 

``` swift 
// Instantiate the URLSession Singleton class, create a url and request

let session = URLSession.shared
let urlString = URL("http://sandipbgt.com/theastrologer/api/horoscope/leo/today")
let url = URL(string: urlString)! 
let request = URLRequest(url: url) 

let task = session.dataTask(with: request) { (data, response, error) in 
    
    func displayError(_ error: String) {
        print(error)
        print("URL at time of error: \(url)")
        performUIUpdatesOnMain { 
            self.setUIEnabled(true) 
        }
    }
}

```
# URL to Components

> When we are constructing our URL it is important that we use URLComponents. 

Note the methods have been updated in Swift 4: 

- NSURLComponents has been renamed to URLComponents.

- NSURLQueryItem has been renamed to URLQueryItem.

Breaking apart your request and each part into their own Components. Below is an example of how this is accomplished in Swift. 

``` swift
import Foundation

// Create an instance of URLComponents
var components = URLComponents()

// Based on RFC 
components.scheme = "https"
components.host = "api.flickr.com"
components.path = "/services/rest"
components.queryItems = [URLQueryItem]() 

let queryItem1 = URLQueryItem(name: "method", value: "flickr.photos.search")
let queryItem2 = URLQueryItem(name: "api_key", value: "1234")
let queryItem3 = URLQueryItem(name: "text", value: "purple")

components.queryItems!.append(queryItem1)
components.queryItems!.append(queryItem2)
components.queryItems!.append(queryItem3)

print(components.url!) 

```

Right now, you're looking at a high level overview of the components structure and how iOS handles URL (or more specifically URIs). However, there is a much better way to understand this with a simple diagram. 

``` javascript

   The following are two example URIs and their component parts:

         foo://example.com:8042/over/there?name=ferret#nose
         \_/   \______________/\_________/ \_________/ \__/
          |           |            |            |        |
       scheme     host       path        query   fragment
          |   _____________________|__
         / \ /                        \
         urn:example:animal:ferret:nose

```

The above illustration is taken from RFC-3986 which details how URI and URLs are broken up in components. 

Basic terminology of terms: 

URN — Unnform Resource Name, the Scheme used, which can be `wss://`, `http://`, `ftp://` etc.
Query - The query can be identified with the ? symbol. 

# Parsing the JSON

# Manipulating the JSON

# Passing the Data

# Updating the UI 

``` swift

if let imageData = try? Data(contentsOf: imageURL!) {
    performUIUpdatesOnMain {
        self.setUIEnabled(true)
        
        // cast the object into a UIImage and set it as the image for the imageView
        self.photoImageView.image = UIImage(data: imageData) 
        
        // set text from data 
        self.photoTitleLabel.text = photoTitle ?? "(Untitled)"
    }
}

```

Why do we want to do this? Well, the simplest explanation is that when you're pulling data from the web, your View will not automatically update on the main thread without first calling this method. Later on, we'll talk more about how asynchronous tasks are handled, and how GCD and updating views on the main thread will make your app work very smoothly. 
