# Kitura-Credentials
A pluggable framework for validating user credentials in a Swift server using Kitura

![Mac OS X](https://img.shields.io/badge/os-Mac%20OS%20X-green.svg?style=flat)
![Linux](https://img.shields.io/badge/os-linux-green.svg?style=flat)
![Apache 2](https://img.shields.io/badge/license-Apache2-blue.svg?style=flat)

## Summary
A pluggable framework for validating user credentials in a Swift server using Kitura


## Table of Contents
* [Swift version](#swift-version)
* [API](#api)
* [Example](#example)
* [List of plugins](#list-of-plugins)
* [License](#license)

## Swift version
The latest version of Kitura-Credentials works with the DEVELOPMENT-SNAPSHOT-2016-03-01-a version of the Swift binaries. You can download this version of the Swift binaries by following this [link](https://swift.org/download/).

## API

The main API of Kitura-Credentials framework is:

```
public func authenticate (credentialsType: String, options: [String:AnyObject]) -> RouterHandler
```

`credentialsType` is the name of credentials plugin (e.g. [Kitura-CredentialsFacebookToken](https://github.com/IBM-Swift/Kitura-CredentialsFacebookToken))
`options` is a dictionary of options passed to the plugin


## Example

This example authenticates post requests using [Kitura-CredentialsFacebookToken](https://github.com/IBM-Swift/Kitura-CredentialsFacebookToken) plugin.

First create an instance of `Credentials` and an instance of credentials plugin:

```
let credentials = Credentials()
let fbCredentialsPlugin = CredentialsFacebookToken()
```
Now register the plugin:
```
credentials.register(fbCredentialsPlugin)
```

And finally call `authenticate` to create a handler for post requests:

```
router.post("/collection/:new", handler: credentials.authenticate(fbCredentialsPlugin.name, options: [:]))
```

## List of plugins:
* [Kitura-CredentialsFacebookToken](https://github.com/IBM-Swift/Kitura-CredentialsFacebookToken)

## License
This library is licensed under Apache 2.0. Full license text is available in [LICENSE](LICENSE.txt).
