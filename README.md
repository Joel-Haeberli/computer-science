# Computer Science Docs

## About

This repository contains a summary of the topics in the IT security specialization at the [Bern University of Applied Sciences](https://www.bfh.ch/en/) and summarizes topics conquered during the Joint Master in Computer Science of the Universities Bern, Neuchâtel and Fribourg [JMCS](https://mcs.unibnf.ch/).

## Browse docs online

- open the link: [Computer Science Docs GitHub Pages](https://joel-haeberli.github.io/computer-science)

The documentation is automatically generated each time new changes are merged into the `main` branch. The workflow is based on [Quartz](https://quartz.jzhao.xyz/), a static site generator built for publishing Obsidian vaults, and then published by [Github-Pages](https://pages.github.com/)

## Open in Obsidian

1. Clone this repository
2. Open the `docs` folder in [Obsidian](https://obsidian.md)

## Build the site locally

1. Install [Node.js](https://nodejs.org/) 22+
2. `npm install`
3. `npm run install-plugins`
4. `node ./quartz/bootstrap-cli.mjs build -d docs -o public --serve` to build and preview at `http://localhost:8080`

## Contribution guidelines

See our [Contribution guidelines](CONTRIBUTING.md)
