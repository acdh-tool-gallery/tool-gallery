# [tool-gallery](https://www.oeaw.ac.at/acdh/newsevents/event-series/acdh-tool-gallery-113)


> Show, don't tell

## Initialize a new dse-static-cookiecutter instance

In this section we are going to build a lightweight static version of [Die Ministerratsprotokolle 1848–1918](https://mrp.oeaw.ac.at/pages/index.html)

1. go to https://github.com/acdh-oeaw/dse-static-cookiecutter
1. read and follow the [Quickstart-Section](https://github.com/acdh-oeaw/dse-static-cookiecutter?tab=readme-ov-file#quickstart)
1. optional: install Python and Cookiecutter
    * e.g. use [uv](https://docs.astral.sh/uv/getting-started/installation/#__tabbed_1_2)
1. open a console
1. initialize the project
    ```shell
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


## Create GitHub Repo and make the initial commit

1. create the GitHub repo that you named in Question 6 (https://github.com/acdh-tool-gallery/mrp-static)
1. go to [https://github.com/acdh-tool-gallery](https://github.com/acdh-tool-gallery) and click on the green button "New"
1. fill out the form
    1. Repository name
        * `mrp-static` same as your answer to Question 1/12
    1. Description
        * static demo version of https://mrp.oeaw.ac.at/pages/index.html
    1. Choose visibility *
        * public (if private you'd need to pay to use GitHub-Actions and GitHub-Pages)
    1. leave the rest and click the green button "Create repository"
1. go back to the console and make sure you are in the `mrp-static` folder
1. run the following commands to initialize a git repo, link it to [https://github.com/acdh-tool-gallery/mrp-static](https://github.com/acdh-tool-gallery/mrp-static) add, commit and push all files
    ```bash
    git init
    git add --all
    git commit -a -m "init commit"
    git branch -M main
    git remote add origin https://github.com/acdh-tool-gallery/mrp-static.git
    git push -u origin main
    ```
    this takes a short while because many files need to be processed/uploaded
1. go to [https://github.com/acdh-tool-gallery/mrp-static](https://github.com/acdh-tool-gallery/mrp-static) 


## Deploy the digital edition via GitHub Pages

1. go to [https://github.com/acdh-tool-gallery/mrp-static/settings/pages](https://github.com/acdh-tool-gallery/mrp-static/settings/pages)
1. from the dropdown list **Build and deployment** select `GitHub Actions`
1. go to [https://github.com/acdh-tool-gallery/mrp-static/actions](https://github.com/acdh-tool-gallery/mrp-static/actions)
1. click on **Deploy static content to Pages** (on the left side)
1. click on the grey button **Run workflow**
    * click on the green button **Run workflow**
1. reload [https://github.com/acdh-tool-gallery/mrp-static/actions/workflows/build.yml](https://github.com/acdh-tool-gallery/mrp-static/actions/workflows/build.yml) and wait for a yellow spinning circle. Click on it and watch how the app is going to be build and deployed (can take 1-2 minutes)
1. when everything is done your app should be online under [https://acdh-tool-gallery.github.io/mrp-static/](https://acdh-tool-gallery.github.io/mrp-static/)


## Develop/adapt/modify the digital edition

This section exemplifies some basic development best practices
* usage of XML-Oxygen and Transformation Scenarios
* usage of variables
* Commit, push and (re)deploy

### correct document title
e.g. [https://acdh-tool-gallery.github.io/mrp-static/toc.html](https://acdh-tool-gallery.github.io/mrp-static/toc.html) makes not much sense

1. check the data, e.g. [https://acdh-tool-gallery.github.io/mrp-static/MRP-3-0-01-0-18670816-P-0044.xml](https://acdh-tool-gallery.github.io/mrp-static/MRP-3-0-01-0-18670816-P-0044.html)

```xml
<titleStmt>
    <title level="s" type="desc">Digitale Edition</title>
    <title level="s" type="main" n="3">Die Protokolle des cisleithanischen Ministerrates 1867–1918</title>
    <title level="s" type="main" n="0"/>
    <title level="a" type="desc" n="044">Nr. 44 Ministerrat (19. Februar 1867–15. Dezember 1867)</title>
    <title level="m" type="main">Band I: 1867</title>
    <title level="m" type="main" n="01">Band 1</title>
    <title level="m" type="sub" n="0"/>
    <title level="m" type="sub">19. Februar 1867–15. Dezember 1867</title>
    <title level="m" type="dates" from="1867-02-19" to="1867-12-15"/>
    <meeting>
        <placeName>Wien</placeName>
        <orgName>Ministerrat</orgName>
        <date when="1867-08-16">1867-08-16</date>
    </meeting>
</titleStmt>
```
1. hope for an easy to extract data point providing good title information
1. `<title level="a" type="desc" n="044">Nr. 44 Ministerrat (19. Februar 1867–15. Dezember 1867)</title>` (actually created beforehand for this tool-gallery)
1. open Oxygen-XML Editor
    1. Project >> Open Project (ctrl + F2)
    1. search for `mrp-static.xpr` and open it
1. open `xslt/toc.xsl`
1. adapt the XPath to the title node
    * `<xsl:value-of select=".//tei:titleStmt/tei:title[1]/text()"/>` -> `<xsl:value-of select=".//tei:titleStmt/tei:title[@level='a']/text()"/>`
1. build toc.html applying an already provided transformation scenario
    * open `data/imprint.xml`
    * click on the wrench symbol (or Document >> Transformation >> Apply|Configure Transformation Scenario)
    * click **Apply associated (1)**
    * check the result in the opened browser window

### fix broken link to document

using a more recent Saxon processor `<xsl:value-of select="document-uri(/)"/> returns nothing; therefore the links and ID column in the table are empty

1. replace
    ```xml
    <xsl:variable name="full_path">
        <xsl:value-of select="document-uri(/)"/>
    </xsl:variable>
    ```
    with
    ```xml
    <xsl:variable name="docId">
        <xsl:value-of select="document-uri(/)"/>
    </xsl:variable>
    ```
1. replace the related code parts
    ```xml
    <xsl:value-of select="replace(tokenize($full_path, '/')[last()], '.xml', '.html')"/>
    ```
    with
    ```xml
    <xsl:value-of select="$docId"/>`
    ```
1. rebuild toc.html (go to imprint.xml and hit strg+shift+T)


### fix title in edition detail view

1. open `xslt/editions.xsl`
2. replace
    ```xml
    <xsl:variable name="doc_title">
        <xsl:value-of select=".//tei:titleStmt/tei:title[1]/text()"/>
    </xsl:variable>
    ```
    with
    ```xml
    <xsl:variable name="doc_title">
        <xsl:value-of select=".//tei:titleStmt/tei:title[@level='a']/text()"/>
    </xsl:variable>
    ```
3. open e.g. `data/editions/MRP-3-0-01-0-18670219-P-0001.xml` and hit strg+shift+T (apply Transformation Scenario)
    1. there is no scenario attached to this file
    1. select "editions" (provided by the cookiecutter)
    1. click on **edit** >> **output** >> check **Open in Browser**
    1. click **OK**
    1. click **Apply**


### persist changes and redeploy

1. commit and push your changes (e.g. using Oxygen-Git Plugin)
1. go to [https://github.com/acdh-tool-gallery/mrp-static/actions/workflows/build.yml](https://github.com/acdh-tool-gallery/mrp-static/actions/workflows/build.yml)
1. click **Run workflow**

## Layout/Design

* basic templating system

### footer

1. adapt/customize `xslt/partials/html_footer.xsl` by replacing existing `<footer></footer> with the snippet below
    ```xml
    <footer class="footer mt-auto py-3 bg-body-tertiary">
        <div class="container-fluid pt-2">
            <div class="row justify-content-center">
                <div class="col-lg-1 col-md-2 col-sm-2 col-xs-6 text-center">
                    <div>
                        <a href="https://www.oeaw.ac.at/acdh/">
                            <img src="images/logo.png" class="footer-logo" alt="ACDH Logo" title="ACDH Logo" />
                        </a>
                    </div>
                </div>
                <div class="col-lg-4 col-md-3 col-sm-3">
                    <div>
                        <p>
                            ACDH
                            <br />
                            Austrian Centre for Digital Humanities
                            <br />
                            Österreichische Akademie der Wissenschaften
                        </p>
                        <p>
                            Bäckerstraße 13
                            <br />
                            1010 Wien
                        </p>
                        <p>
                            T: +43 1 51581-2200
                            <br />
                            E: <a href="mailto:acdh-helpdesk@oeaw.ac.at">acdh-helpdesk@oeaw.ac.at</a>
                        </p>
                    </div>
                </div>
                <div class="col-lg-3 col-md-4 col-sm-3">
                    <div class="row">
                        <div>
                            <span class="fs-6">HELPDESK</span>
                            <br />
                            <p>ACDH betreibt einen Helpdesk mit Rat und Hilfestellung zu verschiedensten Fragen der Digital
                                Humanities.
                            </p>
                            <p>
                                <a href="mailto:acdh-helpdesk@oeaw.ac.at">e-Mail</a>
                            </p>
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-lg-3 col-md-4 col-sm-3">
                            <div class="col-md-4">
                                <a id="github-logo" title="GitHub" href="{$github_url}" class="nav-link" target="_blank">
                                    <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24">
                                        <path
                                            d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-4.466 19.59c-.405.078-.534-.171-.534-.384v-2.195c0-.747-.262-1.233-.55-1.481 1.782-.198 3.654-.875 3.654-3.947 0-.874-.312-1.588-.823-2.147.082-.202.356-1.016-.079-2.117 0 0-.671-.215-2.198.82-.64-.18-1.324-.267-2.004-.271-.68.003-1.364.091-2.003.269-1.528-1.035-2.2-.82-2.2-.82-.434 1.102-.16 1.915-.077 2.118-.512.56-.824 1.273-.824 2.147 0 3.064 1.867 3.751 3.645 3.954-.229.2-.436.552-.508 1.07-.457.204-1.614.557-2.328-.666 0 0-.423-.768-1.227-.825 0 0-.78-.01-.055.487 0 0 .525.246.889 1.17 0 0 .463 1.428 2.688.944v1.489c0 .211-.129.459-.528.385-3.18-1.057-5.472-4.056-5.472-7.59 0-4.419 3.582-8 8-8s8 3.581 8 8c0 3.533-2.289 6.531-5.466 7.59z">
                                        </path>
                                    </svg>
                                </a>
                            </div>
                        </div>
                    </div>
                </div>
                <!-- .-->
            </div>
            <div class="text-center fs-6 fw-lighter">© Copyright OEAW | <a href="imprint.html">Imprint</a>
            </div>
        </div>
    </footer>
    ```
1. adapt `html/css/style.css` by adding
    ```css
    .footer-logo {
        max-width: 50%;
        max-height: 150px;
    }
    ```
1. try out by converting any XML/TEI Dokument via Oxygen
1. commit, push, redeploy

### landing page (index.html)

1. open `xslt/index.xsl`
1. replace `<main> ... </main>`
    with
    ```xml
    <main class="flex-shrink-0 flex-grow-1">
        <div class="container col-xxl-8 pt-3">
            <div class="row flex-lg-row align-items-center g-5 py-5">
                <div class="col-lg-6">
                    <h1 class="lh-base">
                        <span class="display-6"><xsl:value-of select="$project_short_title"/></span>
                        <br/>
                        <span class="display-5"><xsl:value-of select="$project_title"/></span>
                    </h1>
                    <p class="text-end">Demo Applikation, erstellt für die ACDH Tool-Gallery 11.3</p>
                    <p class="lead"> Die Daten stammen von: Stephan Kurz. (2024). oeaw-ministerratsprotokolle/mp-edition-data: v. 1.5 including CMR calendar data 1872–1914 (v.1.5). Zenodo. <a href="https://doi.org/10.5281/zenodo.11484662">https://doi.org/10.5281/zenodo.11484662</a></p>
                    <div class="d-grid gap-2 d-md-flex justify-content-md-start">
                        <a href="search.html" type="button" class="btn btn-primary btn-lg px-4 me-md-2">Volltextsuche</a>
                        <a href="toc.html" type="button" class="btn btn-outline-primary btn-lg px-4">Zu den Protokollen</a>
                    </div>
                </div>
                <div class="col-10 col-sm-8 col-lg-6">
                    <figure class="figure">
                        <img src="images/title-image.jpg" class="d-block mx-lg-auto img-fluid" alt="Friedrich Ferdinand Freiherr von Beust, via Wikimedia Commons" width="400" height="600" loading="lazy"/>
                        <figcaption class="pt-3 figure-caption">Friedrich Ferdinand Freiherr von Beust um 1860; von Autor/-in unbekannt - <a rel="nofollow" class="external free" href="http://www.aeiou.at/aeiou.encyclop.data.image.b/b417372a.jpg">http://www.aeiou.at/aeiou.encyclop.data.image.b/b417372a.jpg</a>, Gemeinfrei, <a href="https://commons.wikimedia.org/w/index.php?curid=1326691">Link</a></figcaption>
                    </figure>
                </div>
            </div>
        </div>
    </main>
    ```
1. download [image](https://de.wikipedia.org/wiki/Friedrich_Ferdinand_von_Beust#/media/Datei:Friedrich_Ferdinand_von_Beust_1860.jpg) and save it as `html/images/title-image.jpg`
    e.g. running
    ```shell
    curl -L "https://upload.wikimedia.org/wikipedia/commons/thumb/1/12/Friedrich_Ferdinand_von_Beust_1860.jpg/594px-Friedrich_Ferdinand_von_Beust_1860.jpg?download" -o html/images/title-image.jpg
    ```
1. add, commit and push
    ```shell
    git add --all
    git commit -a -m "feat(design): landing page"
    git push origin main
    ```

## global settings (params.xsl)

Some answers from the initialisation process are stored in `xslt/partials/params.xsl`. 

1. replace
    ```xml
    <xsl:param name="project_short_title">MRP (statisch)</xsl:param>
    ```
    with
    ```xml
    <xsl:param name="project_short_title">MRP</xsl:param>
    ```
1. rebuild e.g. `index.html`
1. check [http://127.0.0.1:8000/](http://127.0.0.1:8000/)
    * make sure you have a development server up and running
    * `MRP (statisch)` -> `MRP`

## Entities

### customize listperson.html
1. open `xslt/listperson.xsl`
1. open `data/indices/listperson.xml`
1. analyze `data/indices/listperson.xml`
    * z.B. `<person xml:id="mpr2049">`
    * occupation
    * mentions (tei:noteGrp)

1. add new columns to `xslt/listperson.xsl`
    ```xml
    <th scope="col" tabulator-headerFilter="input">Tätigkeit</th>
    <th scope="col" tabulator-headerFilter="input">Erwähnungen</th>
    ```
1. populate those columns
    ```xml
    <td>
        <xsl:value-of select="string-join(.//tei:occupation, ', ')"/>
    </td>
    <td>
        <xsl:value-of select="count(.//tei:noteGrp/tei:note[@type='mentions'])"/>
    </td>
    ```

> [!IMPORTANT]  
> Denormalisation! Make sure that your data provides the information needed to link from an index file to the actual mentions.

#### fix Erwähnt in
1. in `xslt/listperson.xsl` change
    ```xml
    <xsl:if test="./tei:noteGrp/tei:note[@type = 'mentions']">
        <dt>Erwähnt in</dt>
        <dd>
            <xsl:for-each select="./tei:noteGrp/tei:note[@type = 'mentions']">
                <a href="{replace(@target, '.xml', '.html')}">
                    <xsl:value-of select="./text()"/>
                </a>
            </xsl:for-each>
        </dd>
    </xsl:if>
    ```
    to
    ```xml
    <xsl:if test="./tei:noteGrp/tei:note[@type = 'mentions']">
        <dt>Erwähnt in</dt>
        <xsl:for-each select="./tei:noteGrp/tei:note[@type = 'mentions']">
            <dd>
                <a href="{replace(@target, '.xml', '.html')}">
                    <xsl:value-of select="./text()"/>
                </a>
            </dd>
        </xsl:for-each>
    </xsl:if>
    ```
1. style `<dl>` by adding
    ```css
    dd {
    margin-left: 1rem;
    }
    ```
    to `html/css/style.css`



## Full text search (ToDo)


