# Two Factor Authentication-(2FA)-Java [![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](#isc-license)

## Overview:

**Two Factor Authentication-(2FA)-Java** uses Time-based One-time Password ```TOTP``` algorithm.
You can use this code with the ```Google Authenticator``` or the ```Authy``` mobile or browser apps.

* See the [wikipedia page about TOTP](https://en.wikipedia.org/wiki/Time-based_One-time_Password_Algorithm).	
[![CircleCI](https://circleci.com/gh/j256/two-factor-auth.svg?style=svg)](https://circleci.com/gh/j256/two-factor-auth) [![CodeCov](https://img.shields.io/codecov/c/github/j256/two-factor-auth.svg)](https://codecov.io/github/j256/two-factor-auth/)
* Maven packages are published via [![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.j256.two-factor-auth/two-factor-auth/badge.svg?style=flat-square)](https://maven-badges.herokuapp.com/maven-central/com.j256.two-factor-auth/two-factor-auth/)

## To get this to work you:

1. Use `generateBase32Secret()` to generate a secret key in base-32 format for the user.  For example: `"NY4A5CPJZ46LXZCP"`
2. Store the secret key in the database associated with the user account.
3. Display the QR image URL returned by `qrImageUrl(...)` to the user.  Here's a sample which uses GoogleAPIs:

![Sample QR Image](https://chart.googleapis.com/chart?chs=200x200&cht=qr&chl=200x200&chld=M|0&cht=qr&chl=otpauth://totp/user@j256.com%3Fsecret%3DNY4A5CPJZ46LXZCP)

4. User uses the image to load the secret key into his authenticator application.

## Whenever the user logs in:

1. The user enters the number from the authenticator application into the login form on the web server.
2. The web server reads the secret associated with the user account from the database.
3. The server compares the user input with the output from `generateCurrentNumberString(...)`.
4. If they are equal then the user is allowed to log in.

## Maven Configuration

``` xml
<dependencies>
	<dependency>
		<groupId>com.j256.two-factor-auth</groupId>
		<artifactId>two-factor-auth</artifactId>
		<version>1.3</version>
	</dependency>
</dependencies>
```

## **ISC License**

Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted, provided that the above copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
---
---