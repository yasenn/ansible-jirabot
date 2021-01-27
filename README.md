# jirabot

Simple Jira bot built with Ansible and Hashicorp Vault

# Usage

## Create a Task

```
ansible-playbook create.yml
```

It prompts:

  - project
  - summary
  - description
  - business_user

## Add a Comment

```
ansible-playbook comment.yml
```

It prompts:

  - issue key
  - comment line

## Fetch and show JSON

```
ansible-playbook fetch.yml
```

It prompts for the issue key

## Transitions

```
ansible-playbook transition.yml -t progress
```

It prompts for the issue key and moves it to the status 'In Progress' if possible.

```
ansible-playbook transition.yml -t done
```

It prompts for the issue key and moves it to the status 'Done' if possible.

# Requirements

* Ansible
* Hashicorp Vault
* Valid Jira credentials stored in Vault

## Env Vars

* `JIRA_SERVER` - Jira server endpoint
* `VAULT_ADDR` - Vault server endpoint
* `VAULT_TOKEN` - Your Vault token

## Vault creds

K/V's `username` and `password` should be saved either in your `cubbyhole` or in the `services/jira` Vault kv secrets path.

If your credentials not found in your `cubbyhole` then playbook tries to use credentials from `services/jira`.
