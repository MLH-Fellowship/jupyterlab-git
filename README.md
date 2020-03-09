# jupyterlab-git

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/jupyterlab/jupyterlab-git/master?urlpath=lab/tree/examples/demo.ipynb) [![Build Status](https://travis-ci.org/jupyterlab/jupyterlab-git.svg?branch=master)](https://travis-ci.org/jupyterlab/jupyterlab-git) [![Version](https://img.shields.io/npm/v/@jupyterlab/git.svg)](https://www.npmjs.com/package/@jupyterlab/git) [![Version](https://img.shields.io/pypi/v/jupyterlab-git.svg)](https://pypi.org/project/jupyterlab-git/) [![Downloads](https://img.shields.io/npm/dm/@jupyterlab/git.svg)](https://www.npmjs.com/package/@jupyterlab/git) [![Version](https://img.shields.io/conda/vn/conda-forge/jupyterlab-git.svg)](https://anaconda.org/conda-forge/jupyterlab-git) [![Downloads](https://img.shields.io/conda/dn/conda-forge/jupyterlab-git.svg)](https://anaconda.org/conda-forge/jupyterlab-git)<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-15-orange.svg?style=flat-square)](#contributors-)
<!-- ALL-CONTRIBUTORS-BADGE:END -->

A JupyterLab extension for version control using Git

![](http://g.recordit.co/N9Ikzbyk8P.gif)

To see the extension in action, open the example notebook included in the Binder [demo](https://mybinder.org/v2/gh/jupyterlab/jupyterlab-git/master?urlpath=lab/tree/examples/demo.ipynb).

## Prerequisites

- JupyterLab
- Git (version `>=1.7.4`)

## Usage

- Open the Git extension from the _Git_ tab on the left panel

## Install

To install perform the following steps:

```bash
pip install --upgrade jupyterlab-git
jupyter lab build
```

## Settings

Once installed, extension behavior can be modified via the following settings which can be set in JupyterLab's advanced settings editor:

-   **disableBranchWithChanges**: disable all branch operations, such as creating a new branch or switching to a different branch, when there are changed/staged files. When set to `true`, this setting guards against overwriting and/or losing uncommitted changes.
-   **historyCount**: number of commits shown in the history log, beginning with the most recent. Displaying a larger number of commits can lead to performance degradation, so use caution when modifying this setting.
-   **refreshInterval**: number of milliseconds between polling the file system for changes. In order to ensure that the UI correctly displays the current repository status, the extension must poll the file system for changes. Longer polling times increase the likelihood that the UI does not reflect the current status; however, longer polling times also incur less performance overhead.
-   **simpleStaging**: enable a simplified concept of staging. When this setting is `true`, all files with changes are automatically staged. When we develop in JupyterLab, we often only care about what files have changed (in the broadest sense) and don't need to distinguish between "tracked" and "untracked" files. Accordingly, this setting allows us to simplify the visual presentation of changes, which is especially useful for those less acquainted with Git.

### Troubleshooting

Before consulting the following list, be sure the server extension and the frontend extension have the same version by executing the following commands:

```bash
jupyter serverextension list
jupyter labextension list
```

- **Issue**: the Git panel does not recognize that you are in a Git repository.

  Possible fixes:

  - Be sure to be in a Git repository in the filebrowser tab

  - Check the server log. If you see a warning with a 404 code similar to:  
    `[W 00:27:41.800 LabApp] 404 GET /git/server_root?1576081660665`

    Explicitly enable the server extension by running:

    ```bash
    jupyter serverextension enable --py jupyterlab_git
    ```

  - If you are using JupyterHub or some other technologies requiring an initialization script which includes the jupyterlab-git extension, be sure to install both the frontend and the server extension **before** launching JupyterLab.

- **Issue**: the Git panel is not visible.

  Possible fixes:

  - Check that the JupyterLab extension is installed:

    ```bash
    jupyter labextension list
    ```

    If you don't see `@jupyterlab/git v... enabled OK` in the list, explicitly install the jupyter labextension by running:

    ```bash
    jupyter labextension install @jupyterlab/git
    ```

## Development

### Contributing

If you would like to contribute to the project, please read our [contributor documentation](https://github.com/jupyterlab/jupyterlab/blob/master/CONTRIBUTING.md).

JupyterLab follows the official [Jupyter Code of Conduct](https://github.com/jupyter/governance/blob/master/conduct/code_of_conduct.md).

### Install

Requires node 4+ and npm 4+

```bash
# Install new-ish JupyterLab
pip install -U jupyterlab

# Clone the repo to your local environment
git clone https://github.com/jupyterlab/jupyterlab-git.git
cd jupyterlab-git

# Install the server extension in development mode and enable it
pip install -e .[test]
jupyter serverextension enable --py jupyterlab_git

# Build the labextension and dev-mode link it to jlab
jlpm build
jupyter labextension link .
```

To rebuild the package after a change and the JupyterLab app:

```bash
jlpm run build
jupyter lab build
```

To continuously monitor the project for changes and automatically trigger a rebuild, start Jupyter in watch mode:

```bash
jupyter lab --watch
```

And in a separate session, begin watching the source directory for changes:

```bash
jlpm run watch
```

Now every change will be built locally and bundled into JupyterLab. Be sure to refresh your browser page after saving file changes to reload the extension (note: you'll need to wait for webpack to finish, which can take 10s+ at times).

To execute the tests

```bash
pytest jupyterlab_git
jlpm run test
```

## Contributors ✨

The Jupyter Git extension is part of [Project Jupyter](http://jupyter.org/) and is developed by an open community of contributors. To see who has been active recently, please look at the ["Contributors"](https://github.com/jupyterlab/jupyterlab-git/graphs/contributors) tab. Below we list the people and entities who contributed in different ways to the project ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://amazon.com/aws"><img src="https://avatars3.githubusercontent.com/u/2232217?v=4" width="100px;" alt=""/><br /><sub><b>Amazon Web Services</b></sub></a><br /><a href="#financial-aws" title="Financial">💵</a></td>
    <td align="center"><a href="https://github.com/ashutoshbondre"><img src="https://avatars0.githubusercontent.com/u/13174154?v=4" width="100px;" alt=""/><br /><sub><b>Ashutosh Bondre</b></sub></a><br /><a href="https://github.com/jupyterlab/jupyterlab-git/commits?author=ashutoshbondre" title="Code">💻</a> <a href="https://github.com/jupyterlab/jupyterlab-git/pulls?q=is%3Apr+reviewed-by%3Aashutoshbondre" title="Reviewed Pull Requests">👀</a></td>
    <td align="center"><a href="https://github.com/stdlib-js/stdlib"><img src="https://avatars0.githubusercontent.com/u/2643044?v=4" width="100px;" alt=""/><br /><sub><b>Athan</b></sub></a><br /><a href="https://github.com/jupyterlab/jupyterlab-git/commits?author=kgryte" title="Code">💻</a> <a href="https://github.com/jupyterlab/jupyterlab-git/pulls?q=is%3Apr+reviewed-by%3Akgryte" title="Reviewed Pull Requests">👀</a> <a href="#projectManagement-kgryte" title="Project Management">📆</a> <a href="#design-kgryte" title="Design">🎨</a></td>
    <td align="center"><a href="https://github.com/ellisonbg"><img src="https://avatars3.githubusercontent.com/u/27600?v=4" width="100px;" alt=""/><br /><sub><b>Brian E. Granger</b></sub></a><br /><a href="#projectManagement-ellisonbg" title="Project Management">📆</a> <a href="#design-ellisonbg" title="Design">🎨</a> <a href="#ideas-ellisonbg" title="Ideas, Planning, & Feedback">🤔</a> <a href="#fundingFinding-ellisonbg" title="Funding Finding">🔍</a></td>
    <td align="center"><a href="https://github.com/fcollonval"><img src="https://avatars1.githubusercontent.com/u/8435071?v=4" width="100px;" alt=""/><br /><sub><b>Frédéric Collonval</b></sub></a><br /><a href="#maintenance-fcollonval" title="Maintenance">🚧</a></td>
    <td align="center"><a href="https://github.com/hzarea"><img src="https://avatars1.githubusercontent.com/u/27518229?v=4" width="100px;" alt=""/><br /><sub><b>Hana Zarea</b></sub></a><br /><a href="https://github.com/jupyterlab/jupyterlab-git/commits?author=hzarea" title="Code">💻</a> <a href="https://github.com/jupyterlab/jupyterlab-git/pulls?q=is%3Apr+reviewed-by%3Ahzarea" title="Reviewed Pull Requests">👀</a></td>
    <td align="center"><a href="https://github.com/jaipreet-s"><img src="https://avatars1.githubusercontent.com/u/43826141?v=4" width="100px;" alt=""/><br /><sub><b>Jaipreet Singh</b></sub></a><br /><a href="#projectManagement-jaipreet-s" title="Project Management">📆</a> <a href="https://github.com/jupyterlab/jupyterlab-git/pulls?q=is%3Apr+reviewed-by%3Ajaipreet-s" title="Reviewed Pull Requests">👀</a> <a href="https://github.com/jupyterlab/jupyterlab-git/commits?author=jaipreet-s" title="Code">💻</a> <a href="#design-jaipreet-s" title="Design">🎨</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/zzhangjii"><img src="https://avatars3.githubusercontent.com/u/11495372?v=4" width="100px;" alt=""/><br /><sub><b>Ji Zhang</b></sub></a><br /><a href="https://github.com/jupyterlab/jupyterlab-git/commits?author=zzhangjii" title="Code">💻</a> <a href="https://github.com/jupyterlab/jupyterlab-git/pulls?q=is%3Apr+reviewed-by%3Azzhangjii" title="Reviewed Pull Requests">👀</a></td>
    <td align="center"><a href="http://taletskiy.com"><img src="https://avatars0.githubusercontent.com/u/8834829?v=4" width="100px;" alt=""/><br /><sub><b>Konstantin Taletskiy</b></sub></a><br /><a href="https://github.com/jupyterlab/jupyterlab-git/commits?author=ktaletsk" title="Code">💻</a> <a href="https://github.com/jupyterlab/jupyterlab-git/pulls?q=is%3Apr+reviewed-by%3Aktaletsk" title="Reviewed Pull Requests">👀</a></td>
    <td align="center"><a href="https://www.linkedin.com/in/max-klein-b514419"><img src="https://avatars2.githubusercontent.com/u/2263641?v=4" width="100px;" alt=""/><br /><sub><b>Max Klein</b></sub></a><br /><a href="https://github.com/jupyterlab/jupyterlab-git/commits?author=telamonian" title="Code">💻</a> <a href="https://github.com/jupyterlab/jupyterlab-git/pulls?q=is%3Apr+reviewed-by%3Atelamonian" title="Reviewed Pull Requests">👀</a> <a href="#projectManagement-telamonian" title="Project Management">📆</a> <a href="#design-telamonian" title="Design">🎨</a></td>
    <td align="center"><a href="https://github.com/neelamgehlot"><img src="https://avatars2.githubusercontent.com/u/15882916?v=4" width="100px;" alt=""/><br /><sub><b>Neelam Gehlot</b></sub></a><br /><a href="https://github.com/jupyterlab/jupyterlab-git/commits?author=neelamgehlot" title="Code">💻</a> <a href="https://github.com/jupyterlab/jupyterlab-git/pulls?q=is%3Apr+reviewed-by%3Aneelamgehlot" title="Reviewed Pull Requests">👀</a></td>
    <td align="center"><a href="http://noahstapp.com/"><img src="https://avatars0.githubusercontent.com/u/30483654?v=4" width="100px;" alt=""/><br /><sub><b>Noah Stapp</b></sub></a><br /><a href="https://github.com/jupyterlab/jupyterlab-git/commits?author=NoahStapp" title="Code">💻</a> <a href="https://github.com/jupyterlab/jupyterlab-git/pulls?q=is%3Apr+reviewed-by%3ANoahStapp" title="Reviewed Pull Requests">👀</a></td>
    <td align="center"><a href="https://www.saulshanabrook.com/"><img src="https://avatars1.githubusercontent.com/u/1186124?v=4" width="100px;" alt=""/><br /><sub><b>Saul Shanabrook</b></sub></a><br /><a href="https://github.com/jupyterlab/jupyterlab-git/commits?author=saulshanabrook" title="Code">💻</a> <a href="#projectManagement-saulshanabrook" title="Project Management">📆</a> <a href="https://github.com/jupyterlab/jupyterlab-git/pulls?q=is%3Apr+reviewed-by%3Asaulshanabrook" title="Reviewed Pull Requests">👀</a> <a href="#infra-saulshanabrook" title="Infrastructure (Hosting, Build-Tools, etc)">🚇</a></td>
    <td align="center"><a href="https://www.deshaw.com/"><img src="https://avatars0.githubusercontent.com/u/2298205?v=4" width="100px;" alt=""/><br /><sub><b>The D. E. Shaw Group</b></sub></a><br /><a href="#financial-deshaw" title="Financial">💵</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/jupytercalpoly"><img src="https://avatars0.githubusercontent.com/u/19445175?v=4" width="100px;" alt=""/><br /><sub><b>jupytercalpoly</b></sub></a><br /><a href="#financial-jupytercalpoly" title="Financial">💵</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->
<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!

To add yourself, or someone else, to this list you can either [use the bot](https://allcontributors.org/docs/en/bot/usage) (`@all-contributors please add <username> for <contributions>`) or [the CLI](https://allcontributors.org/docs/en/cli/usage) (`jlpm all-contributors add <username> <contributions>`).
