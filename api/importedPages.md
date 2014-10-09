# Imported pages

Imported pages are (navigationally) leaf node pages. A lot of the time they aren't pages at all, but pure native code. The name of each page is listed below together with some information on the input parameters. Most of these pages have been implemented as proof of concept, so they might lack some features and/or have some problems. Please file an issue if you run into anything that seems odd or doesn't work.

The imported pages can be opened using Javascript with only the ```PAGE.openDialog(...)``` method. Trying to open these as a normal page will more than likely fail outright. They are meant to be opened as a dialog natively and will assert or fail in some other way if used incorrectly. Be wary of this if you open any of these pages from a menu item.

---

## Table of contents

* [email](#email)
* [facebook](#facebook)
* [image](#image)
* [message](#message)
* [sinaweibo](#sinaweibo)
* [tencentweibo](#tencentweibo)
* [twitter](#twitter)  

---

## email

Opens an email dialog that uses the email account associated with the phone to send an email.

#### Parameters

```javascript
var args = {
	"toRecipients": string, // comma separated list of emails
	"ccRecipients": string, // comma separated list of emails
	"bccRecipients": string, // comma separated list of emails
	"subject": string, // the subject of the email
	"body": string, // the body of the email
	"html": boolean // true or false if the body is html or not
}

var options = {
	// There are no options that are specific to this page
}

PAGE.openDialog('Email', 'email', args, options);
```

#### Result on iOS

```javascript
{
	"result": number, // The error code
	"error": string // The error in text
}
```

---

## facebook

Allows the user make a Facebook post if the phone has a Facebook account set up.

#### Parameters

```javascript
var args = {
	"text": string // The default text
}

var options = {
	// There are no options that are specific to this page
}

PAGE.openDialog('Facebook', 'facebook', args, options);
```

#### Result on iOS

```javascript
{
	"result": number // The result code
}
```

---

## image

Opens the image selection dialog. This page is very much a proof of concept and could take more parameters.

#### Parameters

```javascript
var args = {
	// Nothing at the moment
}

var options = {
	// There are no options that are specific to this page
}

PAGE.openDialog('Image', 'image', args, options);
```

#### Result on iOS

```javascript
{
	"MediaType": string, // type of media returned
	"URL": string, // url to the media selected
	"MetaData": hash // a hash with metadata for the media selected
}
```

---

## message

Allows the user to send an iOS text message if the user has an account set up.

#### Parameters

```javascript
var args = {
	"recipients": string, // comma separated list of emails
	"subject": string, // the subject of the email
	"body": string // the body of the email
}

var options = {
	// There are no options that are specific to this page
}

PAGE.openDialog('Message', 'message', args, options);
```

#### Result on iOS

```javascript
{
	"result": number // The result code
}
```

---

## sinaweibo

Allows the user to make a Sina Weibo post if the phone has a Sina Weibo account set up and Weibo is present on the phone.

#### Parameters

```javascript
var args = {
	"text": string // The default text
}

var options = {
	// There are no options that are specific to this page
}

PAGE.openDialog('Sina Weibo', 'sinaweibo', args, options);
```

#### Result on iOS

```javascript
{
	"result": number // The result code
}
```

---

## tencentweibo

Allows the user to make a Tencent Weibo post if the phone has a Tencent Weibo account set up and Weibo is present on the phone.

#### Parameters

```javascript
var args = {
	"text": string // The default text
}

var options = {
	// There are no options that are specific to this page
}

PAGE.openDialog('Tencent Weibo', 'tencentweibo', args, options);
```

#### Result on iOS

```javascript
{
	"result": number // The result code
}
```

---

## twitter

Allows the user to make a twitter post if the phone has a twitter account set up.

#### Parameters

```javascript
var args = {
	"text": string // The default text
}

var options = {
	// There are no options that are specific to this page
}

PAGE.openDialog('Twitter', 'twitter', args, options);
```

#### Result on iOS

```javascript
{
	"result": number // The result code
}
```
