# SYTEMS AND ENVIRONMENT TROUBLESHOOTING GUIDE

* **incident id:1**
* **Environment: wsl(ubuntu)/(venv)python/react workspace** 

* **Severity: low(workflow interruption)**

* **Core Focus: POSIX file path resolution and sub system resolution**


## Directory path desynchronization
## SYMPTOM:
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
 
 ## SYMPTOM:`sh:  1: vite: Permission denied`
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

---
# RUST BASED NATIVE COMPILER BINARY MISMATCH
* **incident id:3**
* **environment:wsl(ubuntu)**
* **severity:slightly concerning**
* **core focus:binary mismatch in the compiler**

## SYMPTOM: Cannot find native binding
## CAUSE:
```
Cannot find module '@rolldown/binding-linux-x64-gnu'
code: 'MODULE_NOT_FOUND'
```
## ANALYSIS: Modern vite applications are written in rolldown which needs to be broken down into machine code before use in the specific system, due to previous windows interruption linux couldn't find its package. 
## FIX:` rm -rf node_modules package-lock.json`
### this was neccessary to remove every instance of the unusable packages before re-installing the packages.
## BREAKDOWN:
* **rm**:remove
* **-r**:recursively remove
* **f**:force(skip permissions)
# TAILWIND VERSION 4 MIGRATION
* **incident id:4**
* **environment:wsl(ubuntu)**
* **severity:minimal**
* **core focus:acquiring the new tailwind version**
## SYMPTOM:Invalid command: init
```
Usage: tailwindcss [--input input.css] [--output output.css]
```
### despite using documentation steps `npx tailwind css init -p`
## CAUSE: in the modern tailwind package init was no longer viable
## FIX: