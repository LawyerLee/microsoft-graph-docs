---
title: "Update existing documentation"
description: "Update existing documentation"
localization_priority: Normal
author: "davidmu1"
ms.prod: "microsoft-identity-platform"
doc_type: resourcePageType
---

# Update existing documentation 

All of the following sets of steps are required if you are updating or adding to workload APIs.

- [Set up environment](#set-up-environment)
- [Create or update an API topic](#create-or-update-an-api-topic)
- [Add table of contents (TOC) entries](#add-table-of-contents-entries)
- [Add changelog entries](#add-changelog-entries)
- [Request a technical review](#request-a-technical-review)
- [Request a content review](#request-a-content-review)
- [Publish](#publish)

## Set up environment

1. **(Required if you are new to creating documentation)** Use the information in [Get started with GitHub and Microsoft Graph](https://msgo.azurewebsites.net/add/document/manage-content/get-started-with-github.html) to create a Github account and get started using GitHub.
2. **(Required if you are new to creating documentation)** Choose the tools that you want to use to interact with GitHub:
    - You can use command-line tools to interact with GitHub. For more information, see [Getting Started - The Command Line](https://git-scm.com/book/en/v2/Getting-Started-The-Command-Line).
    - You can use desktop tools to interact with GitHub. For more information, see [GitHub Desktop](https://desktop.github.com/).
    - You can use Visual Studio Code to write markdown files. For more information, see [Markdown and Visual Studio Code](https://code.visualstudio.com/Docs/languages/markdown). For more information about Markdown syntax, see [Docs Markdown Reference](https://review.docs.microsoft.com/help/contribute/markdown-reference?branch=master).
3. **(Required)** Create a working branch in GitHub. Always add or update content through a pull request from a personal branch. Do not use the **Upload files** button on GitHub. If you are submitting a set of changes, be sure to make all your changes in a single branch and not multiple separate branches. This improves processing and publishing efficiency. For more information, see [Manage your documentation on GitHub](https://msgo.azurewebsites.net/add/document/guidelines/manage-your-documentation.html#working-with-git-github-and-the-microsoft-graph-repo).

## Create or update an API topic

1. **(Required)** When planning a new set of beta API documentation, send an email to [Laura Graham](mailto:lauragra@microsoft.com) to provide notification of when the documentation needs to be edited and released. Include in the email the date that the APIs are intended to made available to the public(ship date).
2. **(Optional)** If a new API or resource has been introduced into your existing workload or a large scale update needs to be made to existing API articles (where overwriting the existing articles is preferred over updating them), create initial pages using the stub generator scripts. Microsoft Graph uses CSDL (and XML format) for defining its API surface. The stub generator scripts produce stub markdown files based on the definitions in the CSDL file. Do not change the file names that are generated by the tool. For more information, see [Use the Microsoft Graph REST API docs stub generator](https://msgo.azurewebsites.net/add/document/guidelines/stub-generator.html#scenario-and-usage). 

After you run the stub generation, do not change the generated file name. Do not reorder sections in a generated topic. Do not customize generated table columns.
Copy the API and resource files that you created to the appropriate folders in the working branch that you created.

3. **(Optional)** If you are making changes to existing articles, locate the files in the branch that you created and make the appropriate changes. When adding content, follow these guidelines:
    - For resources, add entries in the **Methods** table for any new methods that are being added to a resource. The method name in the table is linked to the API page that supports the method. Add the return type of the method, and add a description that defines the use of the method.
    - For resources, add entries in the **Properties** table for any new properties that are being added to the resource. The property name, type or the property, and the description of the property are required. If there is more to provide for the description than a table cell can reasonably contain for readability, or, the possible values for the property warrant further explanation, consider creating a separate section with an H3 heading following the properties table. For example, the group visibility options section is an H3 section under the H2 **Properties** section in the group topic. Be sure to document any default properties as described in [Document default properties for entities](https://msgo.azurewebsites.net/add/document/guidelines/default-properties.html).
    - For resources, add entries in the **Relationships** table for any navigational properties that are being added to the resource. The navigational property name, type or the property, and the description of the property are required.
    - For APIs, add the permissions in the table in the permissions section. Make sure that the permissions are also documented in the [Permissions reference topic](https://docs.microsoft.com/graph/permissions-reference).
    - For APIs, verify/edit the HTTP request. add the HTTP header details (optional or required). If no HTTP headers are used, remove the section. Add any additional details regarding the HTTP request/response, as applicable.
    - Format the response payload (JSON) the way that you want. If you want to only show a few properties, set the truncated flag in the comments (right above the response) to `true`.
    - Format the resource JSON representation the way that you want.
    - Verify that the HTTP response code is what is being returned in the API. Complex types are also shown as a resource. These files do not have a **Methods** section.

4. **(Required)** Create the pull request (PR). Set the label of the pull request to **do not merge**. When you receive the build verification email, you’ll be able to preview your content by navigating to your personal branch on the review site: https://review.docs.microsoft.com/en-us/graph/overview?branch=master . (Change “master” to the name of your branch.)  For more information, see the [Add new content or edit existing content](https://msgo.azurewebsites.net/add/document/guidelines/manage-your-documentation.html#add-new-content-or-edit-existing-content) and the [Submit a pull request to the main repository](https://msgo.azurewebsites.net/add/document/guidelines/manage-your-documentation.html#submit-a-pull-request-to-the-main-repository) sections of [Working with GitHub](https://msgo.azurewebsites.net/add/document/guidelines/manage-your-documentation.html).

## Add table of contents entries

**(Required)** Open either the beta or v1.0 toc.yml file in the branch that you created and add table of contents (TOC) entries for the APIs that you are adding. The TOC helps developers locate conceptual and API pages. For more information, see [Microsoft Graph TOC and Topic Title Guidelines](https://msgo.azurewebsites.net/add/document/guidelines/toc-and-topic-title.html).

The following is a YAML example of an entry in the TOC that shows a resource and the methods that can be called on the resource:

```yaml
- name: User
  href: resources/user.md
  items:
    - name: List users
      href: api/user-list.md
    - name: Get user
      href: api/user-get.md
    - name: Create user
      href: api/user-post-users.md
    - name: Update user
      href: api/user-update.md
    - name: Delete user
      href: api/user-delete.md
```

Note that sometimes a method is relevant and exposed in more than one context in the TOC, to show the potential of Microsoft Graph. For example, a user-centric method like sendMail appears under the **Users >> Mail** node and under the **Mail >> Message** node.
Think where your documentation should appear in the TOC, and the TOC titles you want to use. Base this off the existing TOC to maintain consistency across all the content.

## Add changelog entries

**(Required)** Add changelog entries for the APIs and resources that you are adding. For more information, see [Microsoft Graph changelog guidelines](https://msgo.azurewebsites.net/add/document/guidelines/changelog.html).

## Request a technical review

**(Required)** A technical review of the content must be completed before it can be published. The technical review generally creates several actions and changes. The PR review process can be time consuming; however, it is necessary to ensure technical accuracy, compliance, and completeness. To complete a technical review, you invite reviewers in the PR that you created when authoring content. Reviewers can include a content developer, the developer of the API, and the PM for the workload. 

Select **Reviewers** on the **Conversation** page of the PR, and then search for and select the reviewers that you want to include. For more information see, [Requesting a pull request review](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/requesting-a-pull-request-review).

Reviewers that want to request changes to the content can select **Request changes**. This indicates that the PR is not yet ready to merge. When your feedback has been addressed, change the review status on the PR to **Approved**. PRs should only be merged when all reviewers have set the status to **Approved**, but this may not be necessary for all PRs. For more information, see [About pull request reviews](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-request-reviews).

## Request a content review

**(Required)** When the content has been reviewed and revised to be technically accurate, set the label to **content review**. The content review can include a content developer, but always includes the editor who merges PRs. The editor reviews the PR for consistency, compliance, globalization, adherence to guidelines, etc. 

After the review process is complete, incorporate any feedback that was provided in the PR. When all feedback has been incorporated, reviewers have signed off, and the APIs have been released live, set the label to **ready to merge**, enter **#sign-off** as a comment, and then the articles will be published.

## Publish

 PRs that are ready to merge are merged before 3 PM. All API Doctor and OPS build validation tests must pass before merging. At or after 3 PM daily, all PRs that have been merged into the master branch are pulled into the live branch to publish to the site.