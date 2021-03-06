## Introduction
The notifications extension offers methods for event notification over various channels, such as Twitter, email, Pushover and Slack. 

## Setup
To enable notifications simply go to the config.yaml file and change "enable" to true then supply the information below for the channel you would like notifications from.

```yaml
beef:
    extension:
        notifications:
            enable: false
            name: Notifications
            twitter:
              enable: false
              consumer_key: app_consumer_key
              consumer_secret: app_consumer_secret
              oauth_token: your_oauth_token_for_this_app
              oauth_token_secret: your_oauth_token_secret_for_this_app
              target_username: 
            email:
              enable: false
              from_address: sender_email_address
              to_address: receipient_email_address
              smtp_host: 127.0.0.1
              smtp_port: 25
            pushover:
              enable: false
              user_key: pushover_user_key
              app_key: pushover_api_key
            # To enable WebHooks for your Slack workspace,
            # go to: https://slack.com/apps/A0F7XDUAZ-incoming-webhooks
            # Select "Add Configuration", then "Add Incoming WebHooks integration"
            slack:
              enable: false
              webhook_url: "your_webhook_url"
              channel: "#beef"     # Slack channel
              username: "notifier" # Username can be anything
```
## 

***
[[Autorun Rule Engine|Autorun Rule Engine]] | [[BeEF Console|BeEF Console]]