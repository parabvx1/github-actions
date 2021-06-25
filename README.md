# Commit/Pull Request Jira Issue Validation
This Action acts as an integration between GitHub and Atlassian's Jira by ensuring that commits and pull requests in the GitHub repository are linked to valid work items in Jira.

Use Case:
- Commits must include a description that starts with the Jira issue wrapped in square brackets. Ex: "[JIR-1] init commit"
- Pull requests must contain only commits with the above requirement
- Protected branches are used to ensure that merges can only be completed if the Jira issue validation Action succeeds 

The Actions in this repository include:
- # commit_check.yaml: 
  - This Action monitors the specified branch(es) for commit pushes and validates whether the commit includes an active Jira issue in its description. 
  - If a commit is determined to be valid, this Action uses the Atlassian REST API to add a comment onto the Jira ticket, specifying that the commit has been tied to the ticket as active work and including a link back to it.
  - GitHub Secrets is used to store the Atlassian API user, Atlassian API token, and (optionally) the Atlassian instance URL
- # pr_check.yaml:
  - This action monitors the repository for pull requests and validates that all commits included in the pull request include an active Jira issue in their descriptions.
  -  If all commits are determined to be valid, this Action uses the Atlassian REST API to add a comment onto the Jira ticket, specifying that the pull request has been tied to the ticket as completed work and including a link back to it.
