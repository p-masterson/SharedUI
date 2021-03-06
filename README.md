# SharedUI

------

## Prerequisites

This GUI requires Python 3.  It's been tested thoroughly with Python 3.7 and less thoroughly with Python 3.6; versions 3.4 and earlier are incompatible with PyQt5.

Two packages are required:  numpy and PyQt5.  Previous versions of the GUI used PyQt4 instead, but the code is no longer compatible with it.  Installation instructions for PyQt5 can be found [here.](https://doc.bccnsoft.com/docs/PyQt5/installation.html)

Additionally, the [CMS DB loader](https://github.com/valdasraps/cmsdbldr) is now required.  It can be installed with the following commands:

- `pip install ilock`
- `git clone https://github.com/valdasraps/cmsdbldr.git`
- `export PYTHONPATH=$PYTHONPATH:[install-dir]/cmsdbldr/src/main/python`

It's recommended to use Qt Creator for editing the .ui files.  If it's not already installed, you can download it from the Qt Creator tab of [this page.](https://www.qt.io/offline-installers)  After making changes to the .ui files, run the script `compile.sh` (or `compile.bat`) in the .ui files' directory to carry all of the changes over to the corresponding .py files.  (Note:  Adding new .ui files will require you to modify compile.sh and compile.bat accordingly.)

In addition to the above requirements, all users will need a lxplus account.  Furthermore, you will need to add yourself to the cms-hgcal-assemblyOperators [E-group](https://e-groups.cern.ch/e-groups/EgroupsSearchForm.do) in order to get permission to upload to the DB.

## Running and using the GUI

Running the GUI is straightforward:  Run `python mainUI.py` in a terminal to launch it.  On Windows, you can run the batch file `run.bat` instead through either the terminal or the file manager.  All data will automatically be stored as .json files in the directory `/path/to/SharedUI/filemanager_data`.  (Some pages will also produce one or more XML files, but this is still preliminary.)

The GUI is divided into three sections:  Parts, tooling, and supplies; production steps and testing routines; and shipping.

###Parts, tooling, and supplies

Before performing a production step, all necessary parts, tools, and supplies must be created using their respective pages.  For instance, a kapton placement step requires an existing sensor tool, baseplate, sensor component tray, etc.  To create a part, enter the desired part ID into the "[part] ID" box on the corresponding page, then click "New".  It is possible to enter in and save incomplete information for a part, but the production steps will check to make sure that all relevant information has been filled in before allowing the user to save it.

Note that protomodules and modules are automatically createdy by the sensor placement and pcb placement steps, respectively.  They cannot be created manually, but can be edited after creation.  (Some protomodule/module information can't be inherited from their component parts, and has to be entered in manually.)

###Production steps and testing routines

Once all necessary information in the parts, tooling, and supplies section has been filled in, you can proceed to the production steps.  The production step pages are broadly similar to the previous ones, but with one major difference:  the data will be automatically checked for errors, and if any are found, a message will appear in the status box.  Once all errors have been resolved, you can save the step.

Currently, the wirebonding and testing routine pages have not been implemented.

###Shipping

Like the production step pages, the shipping page will display errors unless all of the referenced parts exist.

This step may undergo substantial revision in the future.


WARNING:  Future updates to the GUI will require the [resthub API.](https://github.com/valdasraps/resthub)  (You will need to clone the repo and add `[install-dir]/resthub/clients/python/src/main/python` to your `$PYTHONPATH`.)  However, it's not necessary yet.
