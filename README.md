### venv Setup for Rhino 8 and Grasshopper

#### The 'official' way to install additional libraries for Python 3 in Rhino/GH

Rhino 8 now has support for Python 3. As of today (October 23, 2024) the specific flavor of python used in Rhino/GH is Python 3.9.10. 

Along with the upgrade to python 3, there is now also the ability to (more) easily install external packages. There are a few ways that this functionality is provided in the (very much improved) scripteditor in Rhino/GH. 

There is limited information online for how to do this. The main info I have found is [here](https://discourse.mcneel.com/t/new-python-editor-venv/165673/18) on the McNeel forum from Scott Davidson.

One way is through a special requirement syntax. e.g.

```
# r: numpy
```
or 
```
# requirements: numpy
```

Upon running your script this will use pip to check if the required package is installed. Once the installation procedure is complete you should be able to import your library as usual and use its functionality.

```
# r: numpy

import numpy as np

array = np.array([1,2,3])

print(array)
```
If everything has gone to plan then this should print:

```
[1 2 3]
```

There is also a second way to install packages which involves opening the command prompt. In the command prompt there is a menu item called `Install Package` which will open a nice little installer window. 

![install_pkg](ref/install_packages.gif)

In my experience, these methods of package installation have, so far, been very brittle. There is a way to specify versions of packages, but again, this not well documented.

I have had lots of issues with corrupted environments requiring me to reset the entire python 3 environment. It is also not clear if there is a way to *uninstall* packages installed using this method other than by going into the folder where these packages are installed and deleting the folder directly from there. I am not a big fan of this workflow.

Additionally, when upgrading rhino during minor releases it appears that the python environments are reset and all installed packages are wiped out. This can be quite annoying if you are working with something like pytorch which can take a while to download and install every time you update rhino. 

#### My preferred method for package management takes a different approach


