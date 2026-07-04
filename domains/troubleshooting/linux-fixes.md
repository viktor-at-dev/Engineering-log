# SYTEMS AND ENVIRONMENT TROUBLESHOOTING GUIDE

* **incident id:1**
* **Environment: wsl(ubuntu)/(venv)python/react workspace** 

* **Severity: low(workflow interruption)**

* **Core Focus: POSIX file path resolution and sub system resolution**


## Directory path desynchronization
## When moving a json package for rendering in react the command line threw an error:
``` bash
mv: cannot stat '../emissions_data.json': No such file or directory
 ```
 ## STEP BY STEP ANALYSIS
 ## CAUSE:Terminal execution was in the wrong folder
 `/data-science/emissions-dashboard`
 ## FIX: `../emissions_data.json`
 ## STEP BY STEP SOLUTION:
 
 * **Locate Present Working Directory**:  ((venv) user@the-shop:~/data-science$).

* **Re-map the Path Targets:** Dropped the backward-stepping .. prefix since the file was standing directly inside the current folder scope.

* **Execute Absolute Forward Path**: Targeted the downstream destination by moving the file into the project's internal source folder:


**`mv emissions_data.json ./emissions-dashboard/src/`**
* **Shift Terminal Focus**: Navigated directly into the project repository to synchronize the terminal environment with the React codebase:

Bash
cd emissions-dashboard

## TAKES
* ### .. instructs the cli to go to one level higher than the current directory
* ### ./ instructs the cli to enter  the current folder

---
#  FILE SYSTEM INTERFERANCE
* **incident id:2**
* **Environment:wsl2(ubuntu)**
* **Severity:slightly concerning**
* **core focus:sub system intereferance**
 
 ## PROBLEM:`sh:  1: vite: Permission denied`
 ## ANALYSIS:
 ### The windows system had interrupted the linux system as it was installing the node dependancies leading to the linux system being denied permission to download the npm dependancies as  linux marks the shortcuts for installation in `` node_modules/.bin/`` with a read only file permission mask ``(-rw-r--r--).`` hence upon interruption it was unable to identify the shortcuts
 ---
 ## FIX:
 * Inject execution flags(shortcuts)into the binary files using the ``chmod`` utility

 ``chmod -R +x node_modules/.bin/``
 ## BREAKDOWN:
* ``chmod``:triggers the injection
* ``-R``:makes the injection recursive(repetitive)
* ``+x``:grants executable rights to the injections

 


