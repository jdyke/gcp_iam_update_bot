# GCP IAM Monitor Twitter Bot

Credit to [darkbitio/gcp-iam-role-permissions](https://github.com/darkbitio/gcp-iam-role-permissions) for laying the groundwork to build this bot on top of. 


This repository contains the code for the Twitter bot @name which will tweet when new GCP IAM updates are found.


![Fetch all roles](https://github.com/jdyke/gcp_iam_monitor_bot/workflows/Fetch%20all%20roles/badge.svg)

This repository fetches the ~550 primitive and predefined IAM Roles in JSON format to the `roles` directory.  A GitHub Action is configured to refresh them daily.  This allows for automatic tracking of changes as they are made by GCP.

A couple of helper scripts are provided to aid in searching/listing of the output:

* `list-all-permissions.sh` grabs the unique list of all permissions contained in all roles fetched
* `list-alpha/beta/ga-roles.sh` lists the roles labeled by GCP as alpha, beta, or GA (generally available)
* `list-roles-with-permission.sh <api.resource.verb>` lists the roles that contain a specific permission passed by the first argument. e.g.: `./list-roles-with-permission.sh container.clusters.get`
* `list-permissions-of-role.sh <role.name>` lists the permissions contained by the role named `<role.name>`.  e.g. `./list-roles-with-permission.sh container.admin` (no need to prepend the `roles/`)
