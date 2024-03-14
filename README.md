# Development Coding  standards


# Commits


A well-crafted Git commit message is the best way to communicate context about a change to other developers working on that project, and indeed, to your future self.

This is a specification for adding human and machine readable meaning to commit messages


## Goals

 - Speed ​​up the review process.
 - Help the write process for a good release note.
 - Helping future maintainers.


## SCM is not a backup system
Developers who use it in this way tend to commit at the end of the day, checking everything just there. The result is uselessness, with a generic / random comparison of the code that is impossible for anyone, including the original author, to understand after some time.

## Do not create generic messages (subject)
Do not create any commits labeled as "general fixes and cleanups", "bug fixes" or similar. This type of commit makes it impossible to find out when a bug was introduced, it is difficult to analyze and it makes it practically impossible for anyone else to follow what is happening in the project.

## Use the "Imperative" mode
The purpose of our commit is to say what it did, achieved, not what the developer did, so it makes sense that we use the imperative mode when writing (and not in the past). Another great advantage of this approach is that messages are easier to write and read, and they are more concise. In addition to possibly being smaller in size.
 properly formed Git commit subject line should always be able to complete the following sentence:

If applied, this commit will your subject line here
For example:

- If applied, this commit will refactor subsystem X for readability
- If applied, this commit will update getting started documentation
- If applied, this commit will remove deprecated methods
- If applied, this commit will release version 1.0.0
- If applied, this commit will merge pull request 123 Refactor GetCardUserIds in CardUserManager
Done
 from user/branch
Remember: Use of the imperative is important only in the subject line. You can relax this restriction when you’re writing the body.

Semantic Commit Messages
See how a minor change to your commit message style can make you a better programmer.

Format:

<type>(<scope>): <subject>

<scope> is optional

Example <scope> values:
- init
- runner
- watcher
- config
- web-server
- proxy
- etc.
The <scope> can be empty (e.g. if the change is a global or difficult to assign to a single component), in which case the parentheses are omitted.

The reasons for these conventions:
Automatic generating of the changelog;
Simple navigation through git history (e.g. ignoring style changes);
Communicating the nature of changes to teammates, the public, and other stakeholders.
Triggering build and publish processes.
Making it easier for people to contribute to your projects, by allowing them to explore a more structured commit history.

Example:

feat: add hat wobble
^--^  ^------------^
|     |
|     +-> Summary in present tense.
|
+-------> Type: chore, docs, feat, fix, refactor, style, or test.
More examples:

- feat: (new feature for the user, not a new feature for build script)
- fix: (bug fix for the user, not a fix to a build script)
- docs: (changes to the documentation)
- style: (formatting, missing semi colons, etc; no production code change)
- refactor: (refactoring production code, eg. renaming a variable)
- test: (adding missing tests, refactoring tests; no production code change)
- chore: (updating grunt tasks etc; no production code change)

## Specification

The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be interpreted as described in RFC 2119 .

- Commits MUST be prefixed with a type, which consists of a noun, feat, fix, etc., followed by the OPTIONAL scope, OPTIONAL !, and REQUIRED terminal colon and space.
- The type feat MUST be used when a commit adds a new feature to your application or library.
- The type fix MUST be used when a commit represents a bug fix for your application.
- A scope MAY be provided after a type. A scope MUST consist of a noun describing a section of the codebase surrounded by parenthesis, e.g., fix(parser):
- A description MUST immediately follow the colon and space after the type/scope prefix. The description is a short summary of the code changes, e.g., fix: array parsing issue when multiple spaces were contained in string.
- A longer commit body MAY be provided after the short description, providing additional contextual information about the code changes. The body MUST begin one blank line after the description.
- A commit body is free-form and MAY consist of any number of newline separated paragraphs.
- One or more footers MAY be provided one blank line after the body. Each footer MUST consist of a word token, followed by either a :<space> or <space># separator, followed by a string value (this is inspired by the git trailer convention ).
- A footer’s token MUST use - in place of whitespace characters, e.g., Acked-by (this helps differentiate the footer section from a multi-paragraph body). An exception is made for BREAKING CHANGE, which MAY also be used as a token.
- A footer’s value MAY contain spaces and newlines, and parsing MUST terminate when the next valid footer token/separator pair is observed.
- Breaking changes MUST be indicated in the type/scope prefix of a commit, or as an entry in the footer.
- If included as a footer, a breaking change MUST consist of the uppercase text BREAKING CHANGE, followed by a colon, space, and description, e.g., BREAKING CHANGE: environment variables now take precedence over config files.
- If included in the type/scope prefix, breaking changes MUST be indicated by a ! immediately before the :. If ! is used, BREAKING CHANGE: MAY be omitted from the footer section, and the commit description SHALL be used to describe the -breaking change.
- Types other than feat and fix MAY be used in your commit messages, e.g., docs: updated ref docs.
- The units of information that make up Conventional Commits MUST NOT be treated as case sensitive by implementors, with the exception of BREAKING CHANGE which MUST be uppercase.
- BREAKING-CHANGE MUST be synonymous with BREAKING CHANGE, when used as a token in a footer.

## Examples
- Commit message with description and breaking change footer
feat: allow provided config object to extend other configs

BREAKING CHANGE: `extends` key in config file is now used for extending other config files
## Commit message with ! to draw attention to breaking change
refactor!: drop support for Node 6
## Commit message with scope and ! to draw attention to breaking change
refactor(runtime)!: drop support for Node 6
## Commit message with both ! and BREAKING CHANGE footer
refactor!: drop support for Node 6

BREAKING CHANGE: refactor to use JavaScript features not available in Node 6.
## Commit message with no body
docs: correct spelling of CHANGELOG
## Commit message with scope
feat(lang): add polish language
## Commit message with multi-paragraph body and multiple footers
fix: prevent racing of requests

Introduce a request id and a reference to latest request. Dismiss
incoming responses other than from latest request.

Remove timeouts which were used to mitigate the racing issue but are
obsolete now.

Reviewed-by: Z
Refs: #123
#### References:

- https://www.conventionalcommits.org/ 
- https://seesparkbox.com/foundry/semantic_commit_messages 
- http://karma-runner.github.io/1.0/dev/git-commit-msg.html

# Branch Naming Conventions

## General Rules:
-Branch name should start with the issue tracker identifier ("NNRT-{number}") for Rent and "NNFD-{number}" for Fidelity);
-After the issue tracker Id, we should add a brief description that describes what the branch consists of;
-Words should be in lowercase and separated by hyphens.
### Example:
If I've created a branch to add a validation on the uniqueness of the TaxId from the user being created, I would name the branch in the following way:

NNFD-566-add-taxid-uniqueness-validation-to-user-creation
### Reference:
https://deepsource.io/blog/git-branch-naming-conventions/ 

# Internationalization & Localization
It's importante divide the work properly: we must always be ready to work with multiple languages, and this will be achieved doing some of the work on the client-side, and another part on the server-side.

Our decision is to push part of the internationalisation on sever-side, specially when we are talking about results of API calls. Since the backend has the locale, and is also generating errors, it does make sense to expect localized errors from it. It would also decouple our systems, in a form that, if there is any new feature or change on the backend side, and a new message or error is added, for example, we do not need to replicate this work on all the frontend applications we have and release new versions just because of that.

# Directory Structure 
![image](https://github.com/istarter/development-coding-best-standard/assets/11480617/322b5f7a-d381-492d-937d-f6f5dfc79ec3)


# Linting and Formating Rules
For linting, we use the es lint linter with airbnb rules template as shown below.
This should be the content of the .eslintrc.json file

```

{
	"env": {
		"browser": true,
		"es2021": true
	},
	"extends": [
		"plugin:react/recommended",
		"airbnb",
		"plugin:@typescript-eslint/recommended"
	],
	"parser": "@typescript-eslint/parser",
	"parserOptions": {
		"ecmaFeatures": {
			"jsx": true
		},
		"ecmaVersion": 13,
		"sourceType": "module"
	},
	"plugins": ["react", "@typescript-eslint", "react-hooks"],
	"rules": {
		"indent": ["error", "tab"],
		"no-tabs": 0,
		"react/jsx-indent": [2, "tab"],
		"react/jsx-indent-props": [2, "tab"],
		"react/jsx-filename-extension": [
			"warn",
			{
				"extensions": [".tsx"]
			}
		],
		"no-unused-vars": "off",
		"@typescript-eslint/no-unused-vars": ["error"],
		"no-use-before-define": "off",
		"@typescript-eslint/no-use-before-define": ["error"],
		"import/extensions": [
			"error",
			"ignorePackages",
			{
				"ts": "never",
				"tsx": "never"
			}
		],
		"no-shadow": "off",
		"@typescript-eslint/no-shadow": ["error"],
		"react-hooks/rules-of-hooks": "error",
		"react-hooks/exhaustive-deps": "warn",
		"import/prefer-default-export": "off",
		"react/require-default-props": "off",
		"react/prop-types": "off",
		"react/function-component-definition": [
			2,
			{
				"namedComponents": "arrow-function",
				"unnamedComponents": "arrow-function"
			}
		],
		"react/jsx-props-no-spreading": "off"
	},
	"settings": {
		"import/resolver": {
			"typescript": {}
		}
	}
}

```
# Naming Convention

### Folders and File names:
For folder names, use kebab-case names
- Use app-settings, not AppSettings, not appsettings, not app_settings
For file names kebab-case names, then append the folder name 
- Use article.model.ts, billable-item.model.ts
- Use authentication.service.ts,
- Use english.localization.json, portuguese.localization.json
- Use countries.constants.json

### Components
Components include, atoms, molecules, organisms, routes and pages.

For components file names use camel case.

- Use SideBar.tsx, not sideBar.tsx or Sidebar.tsx
- Use SvgIcon.tsx, not svgIcon.tsx or SVGIcon.tsx (note, do not use uppercase for abbreviations)

### Constants
Use an enum type to define constants,

- The name of the enum must be in camel case, just like you would name a component
- The items in the enum should be in uppercase-snakecase as shown in the example below
 ```

export enum AppRoutes {
  HOME = "/",
  LOGIN = "/Login"
}

```

### Custom Hooks
Prefix the context with the word "use", followed by the camel case name of the context that is being provided

useRequest, useEffectAfterMount
### Higher Other Components
Higher order components are functions that receive components as a parameters and returns a component.

Prefix the HOC name with the word "with", followed by the camel case name of the hoc that is being provided

- withSplashScreen - a HOC that wraps its parameter component with a splash screen. Reuses the splash screen.
- withAnimation - a HOC that applies animations to its parameter component
- withContext - a HOC that provides the application context to the parameter component

# Scrum Guide

## Overview
This document outlines our team's Scrum methodology, detailing our sprint processes, roles, ceremonies, and values essential for agile development.

## Sprints
Sprints are structured periods where specific tasks are completed and reviewed.

### Sprint Plan
- **Goal**: Define achievable deliverables and the necessary work.
- **Duration**: First to the final day of the Sprint.
- **Review**: Demonstrate completed work.

### Sprint Review
- **Objective**: Inspect the sprint's outcome and adjust the product backlog.
  - When: Last day of Sprint.
  - Duration: 1 hour max.

### Sprint Retrospective
- **Objective**: Reflect and improve the Scrum process.
  - What went well, what can be improved.
  - When: Last day of Sprint.
  - Duration: 1 hour max.

## Daily Meeting
- **Objective**: Update and synchronize all team members on current progress.
  - Questions: What did you do yesterday? Are there any impediments? What will you do today?
  - When: Every day.
  - Duration: 15 min max.

### Important Notes:
- Do not wait for late participants in the daily stand-up.
- Respect team time and emphasize the importance of commitments.

## Backlog Refinement
- **Objective**: Clarify backlog items to ensure readiness.
  - The goal is to have items in a "Ready" state, with a clear understanding of implementation and priority.

## Running Sprint Stories
- Maintain clear and transparent communication.
- Keep the sprint goal transparent and avoid misinterpretation of story progress.

## Communication
- **Teams Channel**: Primary platform for Scrum-related communication.
- **Meeting Invites**: Invitations for all Scrum ceremonies will be sent.

## Scrum Values
In July 2016, the Scrum Values were added to the Scrum Guide. These values include:
- Courage
- Focus
- Commitment
- Respect
- Openness

These values help teams about Scrum and deliver amazing software for their customers.

# Team Roles

## Overview
This section outlines the various roles within our Scrum team and their respective responsibilities.

### Product Manager
The Product Manager holds the vision for the product, ensuring that it delivers value to the customer. Responsibilities include:
- Deciding the team's next objectives for delivering more value.
- Writing user stories and acceptance criteria in collaboration with the UX Team and/or Business Analysts.

### Agile Coach
The Agile Coach is tasked with creating an effective and productive work environment and instilling Scrum values, principles, and practices within the team. Responsibilities include:
- Guiding the team in the optimal use of Scrum to build the product.
- Acting as a Facilitator and Servant Leader, promoting self-organization.
- Enabling cooperation across all roles and addressing any issues or non-compliance with Scrum practices.
- Protecting the team from distractions, both external and internal.
- Removing impediments to allow the team to focus on their tasks and adhere to Scrum practices.

### Development Team
The Development Team is a group of professionals responsible for delivering a potentially releasable increment of the product at the end of every Sprint. Characteristics and responsibilities include:
- Building the product according to the sprint goals.
- Functioning as a cross-functional, small, and self-organizing unit that handles development, testing, and release.
- Collaborating to make decisions as a team without a designated lead, ensuring an equal contribution from all members.

**Note:** A successful Scrum Developer is committed to continuous improvement, contributing to the team's success and product development.
