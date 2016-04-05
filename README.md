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






TODO DOC

Setup hockeyapp

Setup slack intergration


## Development

To run locally, clone and then use:

ruby -e "$(curl -fsSL https://raw.github.com/thehackerati/Fuseki/master/setup)" ~/Fuseki

