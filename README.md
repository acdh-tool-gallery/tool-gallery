# [tool-gallery](https://www.oeaw.ac.at/acdh/newsevents/event-series/acdh-ch-tool-galleries)


## Show, don't tell

### Initialize a new dse-static-cookiecutter instance

In this section we are going to build a lightweight static version of [Die Ministerratsprotokolle 1848–1918](https://mrp.oeaw.ac.at/pages/index.html)

1. go to https://github.com/acdh-oeaw/dse-static-cookiecutter
1. read and follow the [Quickstart-Section](https://github.com/acdh-oeaw/dse-static-cookiecutter?tab=readme-ov-file#quickstart)
1. optional: install Python and Cookiecutter
    * e.g. use [uv](https://docs.astral.sh/uv/getting-started/installation/#__tabbed_1_2)
1. open a console
1. initialize the project
    ```bash
    uvx cookiecutter gh:acdh-oeaw/dse-static-cookiecutter
    ```
1. add project specific information (answer the questions)
    1. Q: [1/12] 'directory_name' This folder will be created and is going to hold your awesome code base (dse-static):
        * A: `mrp-static`
    1. Q: [2/12] Some nice title of your Project, will be displayed by default on the start page of your website (Digital Scholarly Editions Static Site Cookiecutter):
        * A: `Die Ministerratsprotokolle 1848–1918 (statisch)`
    1. Q: [3/12] Some short(er) title of your project; shows up by default in the nav bar (DSE Static-Site):
        * A: `MRP (statisch)`
    1. Q: [4/12] Default language of the project. Will be used as lang attribute in the html head elements. Can be customized later (de):
        * A: `de`
    1. Q: [5/12] Either you GitHub User Name, or if you want to host your code repo as part of GitHub Organsiation, the organisation name. This information will be used to generate a link to the code repo of your application (acdh-oeaw):
        * A: `acdh-tool-gallery`
    1. Q: [6/12] You can write whatever URL to your coderepo you want, or you take the default value which is a combination of the 'github_org' and 'directory_name'. (https://github.com/acdh-tool-gallery/mrp-static):
        * A: `https://github.com/acdh-tool-gallery/mrp-static`
    1. Q: [7/12] The URL you have reserved for your website. (https://acdh-tool-gallery.github.io/mrp-static/):
        * A: `https://acdh-tool-gallery.github.io/mrp-static/`
    1. Q: [8/12] The ID of the Redmine-Service-Issue for you application. This is needed to generate an up do date imprint (18716):
        * A: `18716`
    1. Q: [9/12] Should i18n be included to provide translations 1 - no; 2 - yes; Chose from [1/2] (1):
        * A: `1`
    1. Q: [10/12] Ideally data and code is separated. If you want to use the code repo to store/curate the data as well, type 'no' (and just confirm the following questions); If you want to fetch the data from another GitHub Repo confirm, and pay a little more attention to the next questions. [y/n] (y)
        * A: `y`
    1. Q: [11/12] Where is the data for your app stored? Provide the name of a GitHub repo containing your data. Leave it blank to use dummy data or add your data to the code repo later. (dse-static-data):
        * A: `mrp-data`
    1. Q: [12/12] A GitHub repo where the data of you app can be found. The default value is a combination of the answers 'github_repo' and 'data_dir'. (https://github.com/acdh-tool-gallery/mrp-data):
        * A: `https://github.com/acdh-tool-gallery/mrp-data`
1. change into new created directory `mrp-static`
1. run `./fetch_data.sh` to download the data from https://github.com/acdh-tool-gallery/mrp-data into the current project
1. run `ant` to build the website, i.e. converting TEI/XML-Documents into HTML-Files
1. optional: change directory into `html` and start a webserver
    ```shell
    cd html && python -m http.server
    ```
1. optional: visit [http://127.0.0.1:8000/](http://127.0.0.1:8000/)


### Create GitHub Repo and make the initial commit

1. create the GitHub repo that you named in Question 6 (https://github.com/acdh-tool-gallery/mrp-static)
1. go to https://github.com/acdh-tool-gallery and click on the green button "New"
1. fill out the form
    1. Repository name
        * `mrp-static` same as your answer to Question 1/12
    1. Description
        * static demo version of https://mrp.oeaw.ac.at/pages/index.html
    1. Choose visibility *
        * public (if private you'd need to pay to use GitHub-Actions and GitHub-Pages)
    1. leave the rest and click the green button "Create repository"
1. go back to the console and make sure you are in the `mrp-static` folder
1. run the following commands to initialize a git repo, link it to https://github.com/acdh-tool-gallery/mrp-static add, commit and push all files
    ```bash
    git init
    git add --all
    git commit -a -m "init commit"
    git branch -M main
    git remote add origin https://github.com/acdh-tool-gallery/mrp-static.git
    git push -u origin main
    ```
    this takes a short while because many files need to be processed/uploaded
1. go to https://github.com/acdh-tool-gallery/mrp-static 


### Deploy the digital edition via GitHub Pages

1. go to https://github.com/acdh-tool-gallery/mrp-static/settings/pages
1. from the dropdown list **Build and deployment** select `GitHub Actions`
1. go to https://github.com/acdh-tool-gallery/mrp-static/actions
1. click on **Deploy static content to Pages** (on the left side)
1. click on the grey button **Run workflow**
    * click on the green button **Run workflow**
1. reload https://github.com/acdh-tool-gallery/mrp-static/actions/workflows/build.yml and wait for a yellow spinning circle. Click on it and watch how the app is going to be build and deployed (can take 1-2 minutes)
1. when everything is done your app should be online under [https://acdh-tool-gallery.github.io/mrp-static/](https://acdh-tool-gallery.github.io/mrp-static/)