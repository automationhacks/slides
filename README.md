# README

This repo holds markdown slides for different talks given by Gaurav Singh (a.k.a automation hacks) on Test
automation/Testing, and coding

## Talks

### (2020)

- **How to build an automation framework with selenium : patterns and practices**, first delivered
  during Selenium Conference 2020, Bangalore.
  [CFP](https://confengine.com/selenium-conf-2020/proposal/13303/how-to-build-an-automation-framework-with-selenium-patterns-and-practices)
  and slides under `slides/source/docs/ui_automation_framework`

> The slides are automatically served under Github pages. View them
> [online](https://automationhacks.io/slides/index.html)

## Build locally

If you want to build the site locally, clone this repo and then execute below commands

This uses Python
[pipenv to setup dependencies](https://automationhacks.io/2020/07/12/how-to-manage-your-python-virtualenvs-with-pipenv/)
and sphinx as a static site generator

```zsh
# activate pipenv
pipenv shell
# Update the site
make github
# View from local
open build/html/index.html
```
