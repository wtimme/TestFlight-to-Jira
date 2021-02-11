# TestFlight to Jira

Create Jira tickets for app feedback that was submitted through TestFlight.

## Running the script

First, install the dependencies using Bundler: `bundle install`. Next,
configure the project (see below).

Then, simply run `bundle exec fastlane connect_feedback`.

## Screenshot

![Screenshot of a Jira issue that was created from TestFlight feedback](screenshot.png?raw=true)

## Configuration

### Jira

#### Custom field

In order to be able to tell which feedback has already been added to Jira, the script relies on a custom fields in Jira. For the type of this field, I suggest to use "Text Field (read only)". That way, only scripts are able to set the field. (The field does not need to be _visible_ in the screens of your issue. It just has to exist so that the feedback can be referenced.)

Use this custom field as `JIRA_FEEDBACK_ID_FIELD`.

#### Dedicated issue type

Furthermore, I recommend that you add a new issue type (e.g. "TestFlight Feedback") in order to be able to distinguish issues that were created through this script from your regular ones.
Alternatively, you can also just use any other issue type, e.g. "Bug", "Story" or "Task".

Use the ID of the issue type as `JIRA_ISSUE_TYPE_ID`.

## This script

The project is configured through an `.env` file in the `fastlane` directory.

```bash
# The bundle identifier of the app for which to process the feedback
BUNDLE_IDENTIFIER="com.example.app"

# URL to the Jira installation
JIRA_SITE="http://localhost:2990"
JIRA_CONTEXT_PATH="/jira"

# Jira authentication
JIRA_USERNAME="testflight-api-user"
JIRA_PASSWORD="top-secret"

# Key of the project in which the feedback will be created
JIRA_PROJECT_KEY="LOREM"

# ID of the custom Jira field that contains the TestFlight feedback ID.
# This ID is used to identify which feedback items have already been
# added to Jira. The field does not necessarily need to be visible to the user.
JIRA_FEEDBACK_ID_FIELD="10000"

# ID of the issue type in Jira that will be used when creating the feedback.
JIRA_ISSUE_TYPE_ID="10002"

# Your App Store Connect / Apple Developer Portal user
FASTLANE_USER="appleid@example.com"

# Pregenerated session for App Store Connect
# You can obtain this session using `bundle exec fastlane spaceauth -u user@email.com`.
# See: https://docs.fastlane.tools/best-practices/continuous-integration/
FASTLANE_SESSION="---\n- !ruby/object:HTTP::Cookie\n  name: DES5e2f6b4ca4..."
```

## Development

In order to test during development, set up the Jira SDK as pointed out in the [jira-ruby documentation][1].

# License

This repository is licensed under the [MIT license](./LICENSE).

[1]: https://github.com/sumoheavy/jira-ruby#setting-up-the-jira-sdk
