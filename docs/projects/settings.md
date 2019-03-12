Project settings can be accessed by navigating to the `Settings` tab of the project. This page provides the Project Administrators with the Project Name and Hostnames, both of which can be copied to clipboard by clicking the `Copy` button.

![project settings](../images/project_settings.png "Project Settings")

The project settings page also exposes the option to enable and disable project Authentication, as well as an option to delete the project

## Authentication Required

This flag is a project level setting that determines whether clients must first authenticate before managing API Resource or Collection data. If it is **disabled**, anyone with the project links can Create, Read, Update, and Delete project data. If it is **enabled** both API Resources and Collections will require the client to authenticate their requests.

## Delete Project

!!! danger
    Deleting a Project will delete all related data including API Resources, Collections and their associated data, Project Users, API Keys, Logs, and Sessions. **This is a permanent action that can not be undone**.

To delete a project:

1. Be absolutely sure that you want to delete the project, this action is permanent and can not be undone.
2. Click the `Delete Project` button.
3. Confirm you want to delete the project by selecting the `Yes, I'm Sure` button on the confirmation dialog

Your project will then be completely wiped off of the earth and you will be redirected to the project list page.

<br/>
