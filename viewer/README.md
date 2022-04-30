# SADL Model Viewer
SADL files are typically defined, edited, and viewed using the Eclipse IDE with a SADL-file plugin. A browser-based alternative to desktop Eclipse called [Theia](https://theia-ide.org/) is bundled with this repository to allow users to open AM-CDM files using Theia and Docker.

### Viewer Prerequisites
1. `git` - see [installation guide](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
1. `docker-compose`
   - For Windows, follow the [Docker Desktop installation guide](https://docs.docker.com/desktop/windows/install/)
   - For Mac, follow the [Docker Desktop installation guide](https://docs.docker.com/desktop/mac/install/)
   - For Linux, follow the instructions for [installing Docker and `docker-compose`](https://docs.docker.com/desktop/linux/) separately

### Instructions for installing
1. Clone this repository: `git clone https://github.com/kaggour/AM-CDM.git`
1. Enter the cloned directory (`/viewer`) with a Terminal/PowerShell session (the target is the directory that contains the `Dockerfile` and the `docker-compose.yaml` file).
1. With your Docker Desktop application running, enter the command `docker-compose build`. This process will may take several mintues the first time it is run. Subsequent rebuilds will use a cache and run very quickly.

### Instructions for running
1. In the same Terminal/PowerShell session, launch the command `docker-compose up`
1. Once you see a message in the form `root INFO Theia app listening on http://0.0.0.0:3000.` the app is ready to use.
1. Open a web browser, and enter `localhost:3000` in the address bar.
1. In the menu bar that appears in the upper left of the page, select `File` > `Open Workspace` and highlight the directory `SADL` under the `root` folder and click `Open`.
1. Opening the SADL files launches a request for SADL syntax highlighting, and the full color and in-text search functions will activate after ~20 seconds. You can swap through different syntax highlighting schemes by selecting `File` > `Settings` > `Color Theme`

### Note
* Since the `docker-compose.yaml` file shares the a volume with this project's `SADL` directory, any changes you make to the .sadl files in the Theia editor will be reflected on your host directory.
* When launching the Docker container, two files will be created in the SADL directory for the Theia editor to recognize the directory as a SADL project (`.project` and `settings.json`). These files are defined in the project's `.gitignore` file, so they will be excluded from version control.

### Experimental Viewer
To use an experimental version of the viewer with extended functions, replace the `docker-compose` commands above with
* `docker-compose -f docker-compose-exp.yaml build` and
* `docker-compose -f docker-compose-exp.yaml up`
