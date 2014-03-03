# Built in pages

The built in pages can be opened using javascript with the PAGE.openPage or PAGE.openDialog methods. The name of each page is in the list below tougher with some information on the input parameters. Most of these has been implemented as proof of concept and both lack some features as well as might have problems. Please file an issue if you run into anything that seems odd or doesn't work.

# Pages

The pages can be opened as a normal page or as a dialog. For example:

```javascript
PAGE.openPage('Link', 'browser', {link: "https://github.com/reachlocal/liger/blob/master/readme.md"});
```

## browser

Available on iOS and Android.

An in app browser to view web pages rather than LigerMobile pages. For instance opening a link in a message to be viewed inside of the app instead of in an external browser.

```javascript
{
	"link": string, // http(s) link to the webpage
	"allowZoom": boolean // true or false to allow or disallow zoom
}
```

# Pages intended to be opened as dialogs

Trying to open these as a normal page will more than likely fail outright. They are meant to be opened as a dialog natively and will assert or fail in some other way if used incorrectly. Be wary of this if you open any of these pages from a menu item.

For example:

```javascript
var args = {
	toRecipients : "test@test.com, example@example.com",
	ccRecipients : "some@one.com",
	bccRecipient : "example@secret.com"
	subject: "Demoing the email functionality",
	body: "Sent by, LigerMobile",
	html": false
};
PAGE.openDialog('Email', 'email', args);
```

## email

Available on iOS and Android.

Opens an email dialog that uses email account associated with the phone to send the email.

```javascript
{
	"toRecipients": string, // comma separated list of emails
	"ccRecipients": string, // comma separated list of emails
	"bccRecipients": string, // comma separated list of emails
	"subject": string, // the subject of the email
	"body": string, // the body of the email
	"html": boolValue, // true or false if the body is html or not
}
```

Result on iOS.

```javascript
{
	"result": number, // The error code
	"error": string, // The error in text
}
```

## facebook

Available on iOS.

Let's the user make a Facebook post if the phone has a Facebook account set up.

```javascript
{
	"text": string, // The default text
}
```

Result on iOS.

```javascript
{
	"result": number, // The result code
}
```

## image

Available on iOS.

Opens the image select dialog. This page is very much a proof of concept and could take more parameters.

```javascript
{
{
```

Result on iOS.

```javascript
{
	"MediaType": string, // type of media returned
	"URL": string, // url to the media selected
	"MetaData": hash, // a hash with metadata for the media selected
}
```


## message

Available on iOS.

Let's the user send an iOS text message, if the user has an account set up.

```javascript
{
	"recipients": string, // comma separated list of emails
	"subject": string, // the subject of the email
	"body": string, // the body of the email
}
```

Result on iOS.

```javascript
{
	"result": number, // The result code
}
```

## sinaweibo

Available on iOS.

Let's the user make a Sina Weibo post if the phone has a Sina Weibo account set up and Weibo is present on the phone.

```javascript
{
	"text": string, // The default text
}
```

Result on iOS.

```javascript
{
	"result": number, // The result code
}
```

## tencentweibo

Available on iOS.

Let's the user make a Tencent Weibo post if the phone has a Tencent Weibo account set up and Weibo is present on the phone.

```javascript
{
	"text": string, // The default text
}
```

Result on iOS.

```javascript
{
	"result": number, // The result code
}
```

## twitter

Available on iOS.

Let's the user make a twitter post if the phone has a twitter account set up.

```javascript
{
	"text": string, // The default text
}
```

Result on iOS.

```javascript
{
	"result": number, // The result code
}
```
