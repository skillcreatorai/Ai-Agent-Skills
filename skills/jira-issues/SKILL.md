---
name: jira-issues
description: Create, update, and manage Jira issues from natural language. Use when the user wants to log bugs, create tickets, update issue status, or manage their Jira backlog.
license: MIT
---

# Jira Issue Management

Create and manage Jira issues using the Jira REST API or MCP.

## Setup

### Option 1: Jira MCP Server
Install the Jira MCP server for seamless integration:
```bash
npx @anthropic/create-mcp-server jira
```

### Option 2: Direct API
Set environment variables:
```bash
export JIRA_BASE_URL="https://yourcompany.atlassian.net"
export JIRA_EMAIL="your-email@company.com"
export JIRA_API_TOKEN="your-api-token"
```

Get your API token: https://id.atlassian.com/manage-profile/security/api-tokens

## Creating Issues

### Basic Issue
```python
import requests
from requests.auth import HTTPBasicAuth
import os

def create_issue(project_key, summary, description, issue_type="Task"):
    url = f"{os.environ['JIRA_BASE_URL']}/rest/api/3/issue"

    auth = HTTPBasicAuth(
        os.environ['JIRA_EMAIL'],
        os.environ['JIRA_API_TOKEN']
    )

    payload = {
        "fields": {
            "project": {"key": project_key},
            "summary": summary,
            "description": {
                "type": "doc",
                "version": 1,
                "content": [{
                    "type": "paragraph",
                    "content": [{"type": "text", "text": description}]
                }]
            },
            "issuetype": {"name": issue_type}
        }
    }

    response = requests.post(url, json=payload, auth=auth)
    return response.json()

# Example
issue = create_issue("PROJ", "Fix login bug", "Users can't login with SSO", "Bug")
print(f"Created: {issue['key']}")
```

### With Labels and Priority
```python
def create_detailed_issue(project_key, summary, description,
                          issue_type="Task", priority="Medium",
                          labels=None, assignee=None):
    payload = {
        "fields": {
            "project": {"key": project_key},
            "summary": summary,
            "description": {
                "type": "doc",
                "version": 1,
                "content": [{
                    "type": "paragraph",
                    "content": [{"type": "text", "text": description}]
                }]
            },
            "issuetype": {"name": issue_type},
            "priority": {"name": priority},
        }
    }

    if labels:
        payload["fields"]["labels"] = labels
    if assignee:
        payload["fields"]["assignee"] = {"accountId": assignee}

    # ... make request
```

## Common Issue Types

| Type | Use For |
|------|---------|
| Bug | Something broken |
| Task | Work item |
| Story | User-facing feature |
| Epic | Large initiative |
| Sub-task | Part of larger task |

## Updating Issues

### Change Status
```python
def transition_issue(issue_key, transition_name):
    # Get available transitions
    url = f"{JIRA_BASE_URL}/rest/api/3/issue/{issue_key}/transitions"
    transitions = requests.get(url, auth=auth).json()

    # Find matching transition
    transition_id = None
    for t in transitions['transitions']:
        if t['name'].lower() == transition_name.lower():
            transition_id = t['id']
            break

    # Execute transition
    requests.post(url, json={"transition": {"id": transition_id}}, auth=auth)
```

### Add Comment
```python
def add_comment(issue_key, comment_text):
    url = f"{JIRA_BASE_URL}/rest/api/3/issue/{issue_key}/comment"

    payload = {
        "body": {
            "type": "doc",
            "version": 1,
            "content": [{
                "type": "paragraph",
                "content": [{"type": "text", "text": comment_text}]
            }]
        }
    }

    requests.post(url, json=payload, auth=auth)
```

## Searching Issues

### JQL Queries
```python
def search_issues(jql):
    url = f"{JIRA_BASE_URL}/rest/api/3/search"
    params = {"jql": jql, "maxResults": 50}
    response = requests.get(url, params=params, auth=auth)
    return response.json()['issues']

# Examples
my_bugs = search_issues("project = PROJ AND type = Bug AND assignee = currentUser()")
open_items = search_issues("project = PROJ AND status != Done")
recent = search_issues("project = PROJ AND created >= -7d")
```

## Quick Commands

When user says... create this:

| Command | Action |
|---------|--------|
| "log bug about X" | Bug issue with description |
| "create task for X" | Task issue |
| "what's on my plate" | JQL: assignee = currentUser() AND status != Done |
| "move X to done" | Transition issue to Done |
| "add comment to X" | Add comment to issue |

## Best Practices

1. **Summary**: Keep under 80 chars, start with verb (Fix, Add, Update)
2. **Description**: Include steps to reproduce for bugs
3. **Labels**: Use for categorization (frontend, backend, urgent)
4. **Links**: Reference related issues when relevant
