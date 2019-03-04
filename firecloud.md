Using the Broad FireCloud
------------------------------
Eric T Dawson  
Updated: March 2019

## Setup
You'll need Docker and a Java installation to run this tutorial. You can download Docker for you system.

We'll also need to pull the FISS image to push our tool. To get it, run:
```
docker pull erictdawson/fiss
```

We want Cromwell and WOMtool for running and debugging our workflows locally. We can get
them from the GitHub releases page.

```
wget https://github.com/broadinstitute/cromwell/releases/download/36.1/cromwell-36.1.jar
## Aaaand WOMtool
wget https://github.com/broadinstitute/cromwell/releases/download/36.1/womtool-36.1.jar
```


## Dockerizing a tool
See the docker.md tutorial for additional information on dockerizing a tool


## Debugging and running your tool locally

### Testing your Docker container

### Preparing to run your tool in Cromwell


## Notes about imports
There are some important rules about imports:  
1. Imported WDLs must be in FireCloud (GitHub imports are vaporware).
2. Imported WDLs must be publicly readable, and
3. Default WDL permissions are not publicly available, and
4. WDL permissions reset on push, so you need to update them every
time there's a fresh snapshot.
5. WDLs can only be registed on FireCloud if they are a workflow, but
you can use an empty dummy workflow without issue.

## Writing a WDL description


## Pushing to FireCloud
The FireCloud CLI has been deprecated and no longer works, however FISS
(FireCloud Selector Service) is functional if undocumented.

We need to run FISS inside docker. The following command will run FISS and mount your home
directory (at /work) so you can access your WDL files in the container:
```
docker run --rm -it -v "$HOME"/.config:/.config -v "$HOME":/work erictdawson/fiss bash
````

To push a tool to FireCloud using FISS, the command is:
```
fissfc meth_new
```
This both adds new tools and updates existing tools. The full usage is:  
```
fissfc meth_new -d <WDL file> -n <namespace> -m <tool name in FireCloud>
```

## Making tasks and workflows public
1. Navigate to the Method Repository
2. Find and naviagate to the tool page.
3. Click "Permissions"
4. Tick the "Publicly Readable" box.

## Editing your configuration in FireCloud
From the tool's method repository page:
1. Select "Export to Workspace"
2. If no configuration is available, select "Use Blank Configuration"
3. Select you workspace, the entity type, and hit "Export"


In your workspace:
1. Go to the Method Configurations tab and locate your tool.
2. Click "Edit"
3. Update the Snapshot if necessary
4. Fill in the requisite inputs
    - "workspace.*" for workspace-level inputs
    - "this.*" for entity (sample/pair/set/etc) level inputs
    - "this.sample_id" and "this.pair_id" are always available even if you can't see them.

## Running your workflows
1. Select "Launch Analysis" in the top right corner.
2. Select your data to run on.
    - If you are running on a set type:
    in the Expression box, provide an expression. To run a pair method on pairs in a pair_set, for example,
    use "this.pairs" . For the case samples in a case-control, use "this.pairs.control_sample" .

## Important notes
1. The runtime limit of FireCloud is five days
2. Workflows which can run on preemptible instances are much, much cheaper.
