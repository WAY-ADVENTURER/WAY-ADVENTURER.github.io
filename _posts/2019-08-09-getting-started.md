---
title: Getting Started
description: >-
  Get started with Chirpy basics in this comprehensive overview.
  You will learn how to install, configure, and use your first Chirpy-based website, as well as deploy it to a web server.
author: cotes
date: 2019-08-09 20:55:00 +0800
categories: [Blogging, Tutorial]
tags: [getting started]
pin: true
media_subpath: '/posts/20180809'
---

## Creating a Site Repository

When creating your site repository, you have two options depending on your needs:

### Option 1. Using the Starter (Recommended)

This approach simplifies upgrades, isolates unnecessary files, and is perfect for users who want to focus on writing with minimal configuration.

1. Sign in to GitHub and navigate to the starter.
2. Click the <kbd>Use this template</kbd> button and then select <kbd>Create a new repository</kbd>.
3. Name the new repository `<username>.github.io`, replacing `username` with your lowercase GitHub username.

### Option 2. Forking the Theme

This approach is convenient for modifying features or UI design, but presents challenges during upgrades. So don't try this unless you are familiar with Jekyll and plan to heavily modify this theme.

1. Sign in to GitHub.
2. 
3. Name the new repository `<username>.github.io`, replacing `username` with your lowercase GitHub username.

## Setting up the Environment

Once your repository is created, it's time to set up your development environment. There are two primary methods:

### Using Dev Containers (Recommended for Windows)

Dev Containers offer an isolated environment using Docker, which prevents conflicts with your system and ensures all dependencies are managed within the container.

**Steps**:

1. Install Docker:
   - On Windows/macOS, i
   - On Linux, inst
2. 
3. Clone your repository:
   - For Docker Desktop: Start VS Code and 
   - For Docker Engine: Clone your repo [dc-open-in-container] via VS Code.
4. Wait for the Dev Containers setup to complete.

### Setting up Natively (Recommended for Unix-like OS)

For Unix-like systems, you can set up the environment natively for optimal performance, though you can also use Dev Containers as an alternative.

**Steps**:

1. 
2. Clone your repository to your local machine.
3. If you forked the theme, i`bash tools/init.sh` in the root directory to initialize the repository.
4. Run command `bundle` in the root of your repository to install the dependencies.

## Usage

### Start the Jekyll Server

To run the site locally, use the following command:

```terminal
$ bundle exec jekyll serve
```

> If you are using Dev Containers, you must run that command in the **VS Code** Terminal.
{: .prompt-info }

After a few seconds, the local server will be a

### Configuration

Update the variables in `_config.yml`{: .filepath} as needed. Some typical options include:

- `url`
- `avatar`
- `timezone`
- `lang`

### Social Contact Options

Social contact options are displayed at the bottom of the sidebar. You can enable or disable specific contacts in the `_data/contact.yml`{: .filepath} file.

### Customizing the Stylesheet

To customize the stylesheet, copy the theme's `assets/css/jekyll-theme-chirpy.scss`{: .filepath} file to the same path in your Jekyll site, and add your custom styles at the end of the file.

### Customizing Static Assets

Static assets configuration was introduced in version `5.1.0`. The CDN of the static assets is defined in `_data/origin/cors.yml`{: .filepath }. You can replace some of them based on the network conditions in the region where your website is published.

If you prefer to self-host the static assets, re

## Deployment

Before deploying, check the `_config.yml`{: .filepath} file and ensure the `url` is configured correand don't use a custom domain, or if you want to visit your website with a base URL on a web server other than **GitHub Pages**, remember to set the `baseurl` to your project name, starting with a slash, e.g., `/project-name`.

Now you can choose _ONE_ of the following methods to deploy your Jekyll site.

### Deploy Using Github Actions

Prepare the following:

- If you're on the GitHub Free plan, keep your site repository public.
- If you have committed `Gemfile.lock`{: .filepath} to the repository, and your local machine is not running Linux, update the platform list of the lock file:

  ```console
  $ bundle lock --add-platform x86_64-linux
  ```

Next, configure the _Pages_ service:

1. Go to your repository on GitHub. Select the _Settings_ tab, then click _Pages_ in the left navigation bar. In the **Source** section Push any commits to GitHub to trigger the _Actions_ workflow. In the _Actions_ tab of your repository, you should see the workflow _Build and Deploy_ running. Once the build is complete and successful, the site will be deployed automatically.
   

You can now visit the URL provided by GitHub to access your site.

### Manual Build and Deployment

For self-hosted servers, you will need to build the site on your local machine and then upload the site files to the server.

Navigate to the root of the source project, and build your site with the following command:

```console
$ JEKYLL_ENV=production bundle exec jekyll b
```

Unless you specified the output path, the generated site files will be placed in the `_site`{: .filepath} folder of the project's root directory. Upload these files to your target server
