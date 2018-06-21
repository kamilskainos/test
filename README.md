# Welcome to evolve.delivery.integration repository

## Deploying to Iguana

Currently this is a manual process that involves building a deployment package containing translator projects in a zip format and importing them into Iguana channels.

### Building a deployment package

> **The script is intended to be used on local development environments only and should never be run on a Trust environment!**

### Importing transalor zip project

1. Identify the correct channel.
2. On the channel details screen use the Edit Script option.
There are 3 types of translator projects:
* Filter - Edit Script in Filter tab
* To Translator - Edit Script in Destination tab
* From Translator - Edit Script in Source tab
3. Once in the Iguana translator editor, navigate to **main.lua** file and choose **Import Project** option.
4. Import project from zip file.
5. Iguana will detect any changes automatically. Press **Commit to source control** to review those.
6. **You need to make sure that any local configuration or other project dependancies are not being by mistake.**
Any conflicts will need to be resolved before you can commit the changes.
7. Once you are happy with the changes have been reviewed, add a note and **Commit Files**.

## Making changes to Iguana scripts

1. Create a new feature branch.
2. Create new channel(s) or deploy existing from repository.
Currently the deployment process requires a number of manual steps, see instructions below.
3. Make the necessary changes and commit them in Iguana (Iguana uses a separate version control system).
4. Ensure your local feature branch is up to date.
5. Run **pull-from-iguana** script to pull all changes from Iguana into your local git repository (see instructions below).
6. To avoid any conflicts during finalization of the feature branch, ensure that all changes from master are merged to your feature branch.
7. Resolve all conflicts (if any) and commit changes locally.
8. Push changes to remote branch.
9. Open pull request.
10. Once the pull request has been approved (code reviewed) merge changes into the master branch.
11. Delete your feature branch.

## Making changes to other artifacts

Pulling other artifacts back into source control is currently not automated.
Therefore, any changes that are made outside of local repository file structure will need to be manually copied in before pushed to a feature branch.

## Pulling scripts from Iguana

Changes done to scripts via Iguana instance interface can be pulled back automatically using a script. Current version supports both Iguana v5 and Iguana v6. 
<br />All project files will be pulled from Iguana user folder. It's up to you to make sure that only relevant files are uploaded to GitHub by manually deleting any unnecessary additions (e.g. local test channels).
<br />It's worth noting that the script will **ignore** any channels for which the name starts with a **~** character. This allows developers to name their local channels (e.g. used for testing) accordingly and avoid being pulled back into source control.

Supported translator script types:
* :white_check_mark: Filter
* :white_check_mark: To translator
* :x: From translator

### Prerequisites

In order to use the script you will need to have node.js installed locally - visit https://nodejs.org/en/ for more details.

### Running the script

> **The script is intended to be used on local development environments only and should never be run on a Trust environment!**

1. Open command line / terminal and navigate to repository root directory.
2. Download node.js project packages by running: ``` npm install ``` command.
3. To execute the script run: ``` node pull-from-iguana.js ``` command.
4. If the script is run for the first time a default configuration file (config.json) will be created.
You will be asked if to continue with the default configuration:
```
iguana.username = "admin";
iguana.installFolder = "C:\\Program Files\\iNTERFACEWARE\\Iguana";
```
If this is different for you (e.g. you are using a different user account in Iguana), answer no, amend the **config.json file** accordingly and run the script again.
