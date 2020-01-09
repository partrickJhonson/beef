## Summary

* **Objective**: Phish gmail credentials
* **Authors**: floyd
* **Browsers**: Chrome

* [Code](https://github.com/beefproject/beef/tree/master/modules/browser/social_engineering/gmail_phishing)

## Internal Working

User is presented with a login page for gmail. When the user enters credentials they are sent back to beef, and they are redirected to the real gmail login page (where they are prompted for their login again)

```js

beef.execute(function() {
        document.title = "Google Mail: Email from Google";
        beef.browser.changeFavicon("https://www.google.com/mail/help/images/favicon.ico");
        logoutGoogle();
    displayPhishingSite();
});

```


## Screenshots

[[Images/gmail_phish.png|align=center]]


## Feedback

