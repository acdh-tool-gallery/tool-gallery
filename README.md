## [tool-gallery](https://www.oeaw.ac.at/acdh/newsevents/event-series/acdh-ch-tool-galleries)


# Show, don't tell

## Initialize a new dse-static-cookiecutter instance

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
