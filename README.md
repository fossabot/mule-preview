# Mule Preview

[![GitHub License](https://img.shields.io/github/license/agiledigital/mule-preview.svg)](https://github.com/agiledigital/mule-preview-browser-extension/blob/master/LICENSE)
[![CircleCI](https://circleci.com/gh/agiledigital/mule-preview.svg?style=svg)](https://circleci.com/gh/agiledigital/mule-preview)
[![Known Vulnerabilities](https://snyk.io//test/github/agiledigital/mule-preview/badge.svg?targetFile=package.json)](https://snyk.io//test/github/agiledigital/mule-preview?targetFile=package.json)
![npm (scoped)](https://img.shields.io/npm/v/@agiledigital/mule-preview)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fagiledigital%2Fmule-preview.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fagiledigital%2Fmule-preview?ref=badge_shield)

### Summary

This is the core module of the Mule Preview project.

It is a self contained bundle that can be included in other projects
to render Mule XML files in a browser context using React.

See the [Mule Preview Browser Extension](https://github.com/agiledigital/mule-preview-browser-extension) for example usage.

### Instructions

The module exposes four functions that can be used in other projects:

- `mountUrlDiffOnElement(mulePreviewElement, fileAUrl, fileBUrl, contentRoot)`
- `mountUrlPreviewOnElement(mulePreviewElement, fileUrl, contentRoot)`
- `mountDiffOnElement(mulePreviewElement, fileAContent, fileBContent, contentRoot)`
- `mountPreviewOnElement(mulePreviewElement, fileContent, contentRoot)`

where:

- `mulePreviewElement` is an element somewhere in the DOM to mount the Mule Preview React renderer on
- `fileUrl`, `fileAUrl` and `fileBUrl` are URLs to XML files to render or diff
- `fileAContent`, `fileBContent` and `fileContent` are strings containing XML data to render or diff
- `contentRoot` is the a prefix to prepend to any requests for the Mule component image files.

        import {
            mountUrlDiffOnElement,
        } from "mule-preview";

        mountDiffOnElement(
            document.getElementById('root-node'),
            "https://example.com/muleA.xml",
            "https://example.com/muleB.xml",
            "."
        );

### Preparing

On a fresh checkout of the codebase you will need to extract the mappings
and icon assets from Anypoint Studio using [mule-metadata-extractor](https://github.com/agiledigital/mule-metadata-extractor).
        
Download the [latest release of mule-metadata-extractor](https://github.com/agiledigital/mule-metadata-extractor/releases)
and run the following commands:
        
        export ANYPOINT_STUDIO_INSTALLATION=/opt/AnypointStudio  
	java -jar mule-metadata-extractor-1.0.14-standalone.jar -d "${ANYPOINT_STUDIO_INSTALLATION}" -o public/ generate-mappings
	java -jar mule-metadata-extractor-1.0.14-standalone.jar -d "${ANYPOINT_STUDIO_INSTALLATION}" -o public/img/icons extract-images
	java -jar mule-metadata-extractor-1.0.14-standalone.jar-d "${ANYPOINT_STUDIO_INSTALLATION}" -o public/img/icons apply-light-theme

At some point we may provide pre-extracted bundles that can be used with Mule Preview.
We are still unsure about the licencing conditions around bundling and redistributing Mulesoft assets.
We are waiting for a response from Mulesoft. In the meantime feel free to extract the files yourself
for personal use.

### Developing

To work on this module, the following command will mount Mule Preview in a test environment
with hot reloading.

    $ npm start

Simply navigate to http://localhost:8080 in a browser to view the test environment

### Building

Simply run these command to produce a production build

    $ npm run build

The release files will be placed in the "dist" folder

### Acknowledgements

Math icons made by [Freepik](https://www.freepik.com/home) from www.flaticon.com


## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fagiledigital%2Fmule-preview.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fagiledigital%2Fmule-preview?ref=badge_large)