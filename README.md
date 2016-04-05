#Fuseki

Based heavily on Crush & Lovely's iOS boilerplate project Amaro, but tailored for our workflow.

## Usage

Change to your projects directory and run:

ruby -e "$(curl -fsSL https://raw.github.com/thehackerati/Fuseki/master/setup)"


After the prompts:


### Setting up slack integration

Create a new slack channel with your project name.

Go to https://thehackerati.slack.com/apps/manage/custom-integrations

Go to Incoming Webhooks

Add a webhook integration targeting the channel you setup earlier

Copy the webhook url into ./fastlane/Fastfile on the line:

ENV["SLACK_URL"] = "https://hooks.slack.com/services/..."

Run  $ fastlane test

Verify nothing crazy happens

### Setting up the repo

Navigate to https://github.com/new

Follow the prompts to setup as a repo with Hackerati as the owner.

Do not initialize with anything

$ git remote add origin git@github.com:thehackerati/whitelabel.git
$ git push -u origin master


### Setting up hockey

Login to Hockey, select New App, and follow the instructions.

Create an API token with https://rink.hockeyapp.net/manage/auth_tokens

### Setting up travis-ci

https://travis-ci.com/profile/thehackerati

Enable the project repo (you might have to sync to find it on the list)
Add a new ssh-key to travis using

$ ssh-keygen -t rsa -b 4096 -C "operations@thehackerati.com")

and then upload the private key to travis.

Add environment variables for:

MATCH_PASSWORD

FASTLANE_PASSWORD

HOCKEY_API_TOKEN

### Setting up app id

produce -u operations@thehackerati.com -a com.hackerati.WhiteLabel --skip_itc





## Development

To run locally, clone and then use:

ruby -e "$(curl -fsSL https://raw.github.com/thehackerati/Fuseki/master/setup)" ~/Fuseki

