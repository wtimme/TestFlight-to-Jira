# TestFlight to Jira

Create Jira tickets for app feedback that was submitted through TestFlight.

## Configuration

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
```

## Development

In order to test during development, set up the Jira SDK as pointed out in the [jira-ruby documentation][1].

[1]: https://github.com/sumoheavy/jira-ruby#setting-up-the-jira-sdk
