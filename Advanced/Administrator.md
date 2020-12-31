---
layout: page
title: Administrator's Guide
permalink: /internal/administrator
nav_order: 5
---

# Administrator's Guide
{: .no_toc }

This page covers the administrator panel of the researcher console.

**Use caution when accessing this screen**, deleted users' data may not be recoverable and any changes could result in modifications to active studies.

1. TOC
{:toc}

## Accessing the Administrator Panel

If your account has access to the administrator panel, a button labeled _Admin_ will be visible to you in the right of the navigation bar. Clicking it will take you to the panel.

| ![Admin Panel](/img/console/admin.png) |

The panel lists existing users along with their account details and permissions. From here you may modify users' permissions, passwords, and scenarios.

## Modifying User Permissions

To toggle the permissions of a user, click the _Yes_ or _No_ button under the desired permission name. You will be prompted for your password.

| ![User Permissions](/img/console/admin_permissions.gif) |

The number of users allowed admin permission should be minimized as administrators have full access to the resources of all other users.

_Sharing_ permission refers to the ability of a user to share their scenarios and assets with other users.

_Uploads_ permission refers to the ability of a user to upload new animated assets to the system. File uploads are a security risk and so only known users should be granted this permission.

_Hosted Studies_ permission refers to the ability of a user to immediately publish a scenario and generate a live simulation. Users without this permission will need to download their simulation and host it manually on their own webserver.

## Viewing User Details

You may view additional details on a user by clicking the ![Right Arrow](/img/console/button_rightarrow.png) right arrow button next to their username.

| ![User Details](/img/console/admin_details.gif) |

The details pane lists information such as the user's full name, last IP address, and internal ID in the database (information which may be important for developers and for file recovery).

Also listed are all scenarios owned by the user. Clicking on the scenario ID will open the scenario in the editor. Administrators have the ability to modify other users' scenarios. Do not edit other users' scenarios without informing them ahead of time.
