SNIRF MATLAB Readers/Writers
============================

In this folder, you can find MATLAB parsers that can read/write SNIRF formatted data files.

Multiple parsers are stored under this folder. You can choose any one of them for processing
your data.

The currently supported parsers and the respective commands to install/use can be found
in the below sections.

- [General instructions](#general-instructions)
- [EasyH5 HDF5/SNIRF Parser](#easyh5-hdf5snirf-parser)
- [HOMER3 SNIRF Parser](#homer3-snirf-parser)
- [JSNIRF Toolbox](#jsnirf-toolbox)

General instructions
--------------------
You must first add path to the toolbox to be used before you can call their functions in MATLAB.
To do this, you typically need to navigate to the folder that contains this toolbox, for example,
if the toolbox was checked out as part of the `snirf` repository, then you should run
```
  cd /path/to/snirf/lib/matlab
```
make sure the toolbox is a subfolder in the path above. Then, you can use the below command to
add the path
```
  addpath('toolbox_folder_name')
```
If you want to add this path permanently, you need to type `pathtool`, 
browse and select the toolbox folder and add to the list, then click "Save".
Then, run `rehash` in MATLAB to use the functions.

If you use MATLAB in a shared environment such as a Linux server, the
best way to add path is to type 
```
   mkdir ~/matlab/
   nano ~/matlab/startup.m
```
and type addpath('/path/to/toolbox') in this file, save and quit the editor.
MATLAB will execute this file every time it starts.

EasyH5 HDF5/SNIRF Parser
--------------------
* Folder: `easyh5`
* Author: Qianqian Fang <q.fang at neu.edu>
* Version: 0.8

### How to install
Following the above general instruction, and run the below command in MATLAB to use
this toolbox:

```
  addpath('easyh5')
```
### How to use

Loading SNIRF file:
```
  data=loadh5('datafile.snirf');                % .snirf is the same as .h5
  data=loadh5('datafile.snirf', 'regroup',1);   % regroup flag merge data into cell/struct array, recommended
```

Saving SNIRF file:
```
  saveh5(snf, 'datafile.snirf');   % snf must be a snirf structure containing {'formatVersion','nirs'} subfield
  saveh5(snf, 'datafile.snirf','compression','deflate');   % use 'compression' flag to save data with compression to save space
```


HOMER3 SNIRF Parser
--------------------
* Folder: `snirf_homer3`
* Author: Jay Dubb <jdubb at bu.edu>
* Version: 1.13.4

### How to install
Following the above general instruction, and run the below command in MATLAB to use
this toolbox:

```
  addpath(genpath('snirf_homer3'))
```

alternatively, you can use 
```
  cd /path/to/snirf_homer3/
  setpath
```


JSNIRF Toolbox
--------------------
* Folder: `jsnirfy`
* Author: Qianqian Fang <q.fang at neu.edu>
* Version: 0.4

### How to install
This toolbox provides easy-to-use snirf/jsnirf functions. It requires the installation
of EasyH5 toolbox.

Following the above general instruction, and run the below command in MATLAB to use
this toolbox:
```
  addpath('jsnirfy')
  addpath('easyh5')
```
### How to use

Loading SNIRF file:
```
  data=loadsnirf('datafile.snirf');            % this is the same as loadh5(..,'regroup',1);
```

Saving SNIRF file:
```
  savesnirf(snf, 'datafile.snirf');   % snf must be a snirf structure containing {'formatVersion','nirs'} subfield
  savesnirf(snf, 'datafile.snirf','compression','deflate');   % use 'compression' flag to save data with compression to save space
```

Create an empty SNIRF data struture
```
  snf=snirfcreate;
  snf=snirfcreate('data',mydata,'aux',myaux);
```

Create a JSNIRF data struture
```
  snf=jsnirfcreate;
  snf=jsnirfcreate('data',mydata,'aux',myaux);
```