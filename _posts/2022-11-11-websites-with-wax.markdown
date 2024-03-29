---
layout: post
title: "Websites with Wax"
author: "Alison Harvey"
date: 2022-11-11
---
One of the reasons I was keen to [develop a blog using Jekyll](https://aeh0.github.io/experiiiments/2022/08/04/blog-like-a-hacker.html), was in order to learn more about [Wax](https://minicomp.github.io/wiki/wax/). Wax builds on Jekyll's foundations - it's a workflow that can be used make a configurable, static website with only a folder of images and a spreadsheet of image metadata. 
<!--more-->
As with Jekyll-based blogs, [websites made with Wax](https://minicomp.github.io/wax/) are free to set up and host using GitHub pages, offer flexibility, freedom from ads and branding, and are particularly suitable for hosting high-quality image collections and scholarly exhibits. It's possible to embed pre-existing IIIF content in iframes, as on any other website, but Wax can also be used to create and serve IIIF-compliant images, at no cost. Standard tifs and jpegs are added to the site, transformed into IIIF tiles, compiled into multi-page objects, and made accessible in an [OpenSeaDragon viewer](https://openseadragon.github.io/). This allows anyone to host a free website featuring IIIF content, with no underlying infrastructure.

I set up a [simple demo](https://aeh0.github.io/wax-demo/), starting with just six digital objects with their metadata. I used a couple of photos, poems, and multi-page letters from the [Edward Thomas archive](https://archiveshub.jisc.ac.uk/data/gb1239-424), held at [Special Collections and Archives, Cardiff University](https://www.cardiff.ac.uk/special-collections).

The images can be filtered (for example, into photos, poems, or letters) via the [homepage](https://aeh0.github.io/wax-demo/), or via the [Browse](https://aeh0.github.io/wax-demo/collection/) page. The metadata attached to the images can be keyword searched via the [Search](https://aeh0.github.io/wax-demo/search/) page - results update responsively as keywords are entered. An Exhibits collection holds sample pages featuring illustrated narratives in markdown. These support html iframes - allowing the inclusion of pre-existing IIIF content, as well as the IIIF-images generated by Wax. One example demonstrates [text wrapped around a Universal Viewer, embedded in an iframe](https://aeh0.github.io/wax-demo/exhibits/b/), while the other uses an [inline parallax image - a jpeg tiled by Wax for IIIF delivery](https://aeh0.github.io/wax-demo/exhibits/a/). 

The results look very professional, and I've learned a lot of fundamental computing skills in the process. Wax offers a means of learning the basics of web development, metadata creation and management, and plain text editing. I'm continuing to experiment with configuring the site's appearance, and researching options for supporting bilingual content.

## The technical bit

# Creating metadata

* Wax can work with CSV, JSON, and YAML metadata files, though CSV is recommended. Create your CSV in Google Sheets rather than Excel, which can cause encoding errors. 
* Every row in the spreadsheet will represent a digital object. 
* The only mandatory columns are **pid** and **label**. 
* **Pid** is the persistent identifier for each digital object. It must be unique. Use lowercase, don't include spaces, and keep the identifiers simple, e.g. poem001.
* **Label** is the title for each digital object. This should be a succinct description, which will be displayed on your site, e.g. 'The Ash Grove, 1916'.
* You can add as many other descriptive metadata fields/spreadsheet columns as you like. Keep the field names in lowercase, avoid special characters, except underscores, which should be used rather than spaces. Fields only need to make sense to you - you can change how they will display on your site later.
* Some field names will cause confusion with the underlying software of Jekyll and Wax. Avoid **id** (use **pid** instead), **date** (use **_date** instead), and **tags** for filtering (use **object_type** instead).
* I used **pid**, **label**, **author**, **description**, and **_date** to describe each object, and **object_type** to add a tag/category, allowing the objects to be filtered (see table below).
* Export the metadata file in csv format, saving locally it with a simple name, e.g. **metadata.csv**

| pid  | label                            | author        | description                 | _date       | object_type |
| ---- | -------------------------------- | ------------- | --------------------------- | ----------- | ----------- |
| obj1 | The Ash Grove, 1916              | Edward Thomas | Manuscript, second draft... | 1916        | poem        |
| obj2 | Blenheim Oranges, 1916           | Edward Thomas | Manuscript draft in ink...  | 1916        | poem        |
| obj3 | 17 Oct 1897                      | Edward Thomas | Letter from...              | 17 Oct 1897 | letter      |
| obj4 | 14 Nov 1897                      | Edward Thomas | Letter from...              | 14 Nov 1897 | letter      |
| obj5 | Turner's Tower, Somerset, 1913   | Edward Thomas | Image of...                 | 1913        | photo       |
| obj6 | Alresford, Winchester, 1913      | Edward Thomas | Image of...                 | 1913        | photo       |

# Preparing images

 * Wax accepts .tiff, .jpeg, .png, and .pdf files and assumes relatively high resolution. For best results, resolution should be as standard as possible across the collection.
 * For Wax to work, each source image file must be named to match its pid in the metadata exactly. 
 * A single image objects, such as **obj1**, must be named **obj1.jpg**. 
 * A multi-page object, such as **obj3**, must be stored in a folder called **obj3**, and contain images with a running filenumber, according to the order you want the images to appear, e.g. page 1 = **001.jpg**, page2 = **002.jpg**, etc.
 * Store all your images and any related folders in one single folder locally. Name it simply - mine was **edward**.

# Setting up your system

* Install a text editor if you don't have one. [Atom](https://atom.io/) or [Visual Studio Code](https://code.visualstudio.com/) are good options. You will also need [GitHub Desktop](https://desktop.github.com/).
* Install [Docker and Git](https://minicomp.github.io/wiki/wax/setting-up-your-system/with-docker/). I originally attempted to [install the five individual software components manually](https://minicomp.github.io/wiki/wax/setting-up-your-system/install-manually/), but some of the instructions in the documentation are out of date. Installing Docker, where all of the required software is pre-bundled into one container, worked without any issues. 
* Open your command prompt and check that Docker and Git are correctly installed:

~~~
docker -v
git -version
~~~

# [Creating your own Wax repository](https://minicomp.github.io/wiki/wax/setting-up-your-site/copy-the-demo-template/)

* Log into [GitHub](https://github.com), or register a new account 
* Go to the [Wax repository](https://github.com/minicomp/wax) and click **Use this Template** (green button) > **Create a new repository**.
* This prompts you to create a copy of the repository, attached to your own account. You should name it after the collection or exhibition you’ll make, since this name will be displayed in your free URL for the project with GitHub. I called mine **wax-demo**.
* Go to your new Wax repository page, click the green **Code** button, and copy the URL it provides to your clipboard. This should look like: https://github.com/[YOUR_GITHUB_USERNAME]/[YOUR_REPOSITORY_NAME].git
* Open command prompt, and change directory into where you’d like to work on your project, e.g.

~~~
cd Documents
~~~

* Run the git clone command plus the link you copied in one line, e.g.

~~~
git clone https://github.com/[YOUR_GITHUB_USERNAME]/[YOUR_REPOSITORY_NAME].git
~~~

# [Building the site](https://minicomp.github.io/wiki/wax/using-docker/)

* Open Docker Desktop. I couldn't work out where to go to build the image, but right-clicking on the Docker Desktop icon in the system tray, and launching **Quick Start Guide** worked for me. Click Start, and use the new terminal on the right to build the site.

* First, change directory into your newly cloned project folder, which will be the same as your repository name, e.g.

~~~
cd wax-demo
~~~

* Build the minicomp/wax base Docker image (don't forget the "." at the end!) You only need to do this once.

~~~
docker build -t minicomp/wax .
~~~

* Every time you want to build a new Wax site, you can create and access an interactive bash container from the image by running:

~~~
docker run -it --rm -v ${PWD}:/wax --name wax -p 4000:4000 minicomp/wax bash
~~~

* Inside the container, update the dependencies by running:

~~~
bundle update
~~~

* Check that you have the wax_tasks available by running:

~~~
bundle exec rake --tasks
~~~

* This will display a summary list of all the things Wax can do. Leave the terminal open while you add your collection data to the repository.

# [Adding your collection data](https://minicomp.github.io/wiki/wax/setting-up-your-site/adding-your-collection-data/)

* Open File Explorer, and navigate to your new Wax repository.
* Start by deleting the template data. Delete the **_qatar** folder. Open the **img** folder and delete the **derivatives** folder inside. Open the **_data** folder and delete the csv files. Then open the **raw_images** folder and delete the contents.
* Next, add your top-level image folder and all of its contents, e.g. **edward** to the **raw_images** folder, then one level up, add your **metadata.csv** file to the **_data** folder.

# [Updating your configuration](https://minicomp.github.io/wiki/wax/setting-up-your-site/updating-your-configuration/)

* At the top level of the repository, open the **_config.yml** file in your text editor. Update the title, description, copyright, url (e.g 'https://[YOUR_GITHUB_USERNAME].github.io') and baseurl (e.g. '/[YOUR_REPOSITORY_NAME]') with your own details.
* Further down the code, in **COLLECTION SETTINGS**, update all instances of **qatar** to the name of your image folder (e.g. **edward**). Check the collection name, layout, and raw_images path. Update metadata source to the name of your csv file. The template data looks like:

~~~
collections:
  exhibits:
    output: true
  qatar:
    output: true
    layout: 'qatar_item'
    metadata:
      source: 'qatar.csv' # path to the metadata file within `_data`
    images:
      source: 'raw_images/qatar' # path to the directory of images within `_data`
~~~

* I changed mine to look like this: 

~~~
collections:
  exhibits:
    output: true
  edward:
    output: true
    layout: 'edward_item'
    metadata:
      source: 'metadata.csv' # path to the metadata file within `_data`
    images:
      source: 'raw_images/edward' # path to the directory of images within `_data`
~~~

* In **SEARCH INDEX SETTINGS**, update the word **qatar**, and the list of fields to reflect the ones you've used. Only include fields you want to make searchable. Mine looks like: 

~~~
search:
  main:
    index: '/search/index.json' # file the index will get written to
    collections:
      edward:
        content: false # whether or not to index page content
        fields: # the metadata fields to index
          - label
          - author
          - description
          - _date
          - object_type
~~~

* Further down, you can configure the **MENU** and **FOOTER** for your site, but this can be done at any stage.

* The layout **edward_item**, referred to in the **COLLECTIONS** code, didn't exist, so I needed to create it. Go to **_layouts**, and open the **qatar_item** layout in a text editor. Rename it to **[YOUR_IMAGE_FOLDER NAME]_item**, and update the content related to labels and values. The values are the names of the field names you've chosen, and the labels the text that you want to display on your site. Mine looks like:

~~~
meta:
  - label: 'Title'
    value: page.label
  - label: 'Author'
    value: page.author
  - label: 'Description'
    value: page.description
  - label: 'Date'
    value: page._date
  - label: 'Type'
    value: page.object_type
~~~

* If you want to add links to your metadata, add **type: link** underneath the value.

* Check the **index.md** file, and the contents of **_pages**, removing any references to **qatar**, and configuring as required.

# Running the tasks - create IIIF images

Go back to Docker, and run:

~~~
bundle exec rake wax:derivatives:iiif [YOUR_COLLECTION_NAME]
~~~

When you run the line above for your collection, the task will:
1. Look for the directory of source images you specified in your **_config.yml** file under collections > [YOUR COLLECTION_NAME] > images > source.
3. Generate many IIIF derivatives, image tiles, and JSON representations of the collection items into the directory **img/derivatives/iiif**.
4. Automatically add three fields (full, thumbnail, and manifest) to each of your metadata records with the relative paths to the full and thumbnail size image derivatives and the IIIF manifest.

# Running the tasks - create collection pages

In Docker, run:

~~~
bundle exec rake wax:pages [YOUR_COLLECTION_NAME]
~~~

This will:
1. Look for the metadata file you specified in your **_config.yml** file under collections > [YOUR_COLLECTION_NAME] > metadata > source.
2. Generate a directory named after your collection prepended with an underscore (e.g., _[YOUR_COLLECTION_NAME]).
3. Generate pages into that directory for each record, named after its pid value.

# Running the tasks - create the search index

In Docker, run:

~~~
bundle exec rake wax:search [YOUR_SEARCH_NAME]
~~~

Your **search name** is the word found under 'search' in the **SEARCH** section of your config.yaml file, e.g. **main**

This will:
1. Look for the search configuration you set up in your **_config.yml** file.
2. For each collection you gave the search, it will look for the markdown pages, and add the fields and/or content from each page to the index.
3. It will write the index as a JSON file to the filename you gave (e.g. **/search/index.json**).

* You're finished with Docker. You can exit by typing the command 'exit', which will destroy the container but not the base image. You can create and accessing a new container whenever you want to create a new Wax site by running the command below, updating the dependencies, and checking the tasks are available:

~~~
docker run -it --rm -v ${PWD}:/wax --name wax -p 4000:4000 minicomp/wax bash
bundle update
bundle exec rake --tasks
~~~

# Configuration

Further configuration can be applied through the use of [theme layouts](https://minicomp.github.io/wiki/wax/using-theme-layouts/) and [components](https://minicomp.github.io/wiki/wax/using-theme-components/).

# Make your site live via GitHub Pages

* So far, you've been working on files stored locally. You need to send copies of these to GitHub. Open GitHub Desktop, and click on New > Create a repository. Enter the name of your repository, and you will be be prompted to 'add this repository'. Click this, and confirm. Enter 'new site' in the summary box, and commit to main. Finally, push commit to the origin remote. In a few minutes, your online files will match your local files. In GitHub, go to your repository's 'Action' tab to see the workflow run live.
* When completed, go to the Settings tab > Pages.
* Under Source, select 'deploy from a branch' and set 'branch' to 'main/(root)', then click 'save'.
* Wait a few minutes for site to build. When you refresh the page, it should now say, 'Your site is published at https://[YOUR_USERNAME].github.io/[YOUR_REPOSITORY_NAME]'. Congratulations - your site is live!
