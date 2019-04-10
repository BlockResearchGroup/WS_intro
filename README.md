[COMPAS](https://compas-dev.github.io) | [COMPAS main repo](https://github.com/compas-dev/compas) | [COMPAS main docs](https://compas-dev.github.io/main/)

# Workshop: COMPAS introduction

## Requirements

* Operating System: Mac (OSX) or Windows
* [Anaconda Python Distribution](https://www.anaconda.com/download/): 3.7
* [Rhino](https://www.rhino3d.com/)
* Code editor: We recommend [VS Code](https://code.visualstudio.com/) for this workshop.
* Git: [official command-line client](https://git-scm.com/)

> **Note**
>
> If you use Rhino 5.0 on Windows, make sure to install the following
> 
> * [Grasshopper](https://www.grasshopper3d.com/)
> * [GHPython](https://www.food4rhino.com/app/ghpython)
> * [IronPython 2.7.5](https://github.com/IronLanguages/main/releases/tag/ipy-2.7.5)
    ([see here for details about this manual update](https://compas-dev.github.io/main/environments/rhino.html#ironpython-1)).

## Getting started

We will install **COMPAS** using *conda*, the package manager of Anaconda.
Anaconda uses *environments* to create isolated spaces to manage the various dependencies and requirements of different projects.

**1. Clone the workshop repository.**

* On Windows: launch Anaconda Prompt (**as administrator**)
  <br />On Mac: launch Terminal
* Go to the destination folder where you wish to place all the workshop material
* Run `git clone https://github.com/BlockResearchGroup/WS_intro.git`

> **Example**
>
> On Windows
> ```bash
> mkdir %USERPROFILE%\Code
> cd %USERPROFILE%\Code
> mkdir Workshops
> cd Workshops
> git clone https://github.com/BlockResearchGroup/WS_intro.git
> ```
>
> On Mac
> ```bash
> mkdir ~/Code
> cd ~/Code
> mkdir Workshops
> cd Workshops
> git clone https://github.com/BlockResearchGroup/WS_intro.git
> ```

**2. Install COMPAS.**

```bash
conda conda config --add channels conda-forge
conda install COMPAS
```

> **On Mac**
>
> In addition to the above commands, on Mac you will also need to install `python.app`
> Don't ask, long story :)
> ```bash
> conda install python.app
> ```

**3. Check the installation**

Launch the Python interpreter and import `compas`, `compas_rhino`, `compas_ghpython`.

On Windows: type `python` in Anaconda Prompt
<br />On Mac: type `python` in Terminal

```python
>>> import compas
>>> import compas_rhino
>>> import compas_ghpython
```

If no error messages appear, you're good to go.
Type `exit()` to quit the interpreter.
The packages `compas`, `compas_rhino`, `compas_ghpython` are
now installed in your environment, and will be available in Python if the workshop environment
is active.

**4. Configure Rhino**

To make the installed packages available in Rhino,
run the following from Anaconda Prompt (on Windows) or Terminal (on Mac):

```bash
python -m compas_rhino.install -v 5.0 -p compas compas_rhino compas_ghpython
```

> **Note** (Windows only)
>
> Use `-v 6.0` instead of `-v 5.0` if you want to use Rhino 6 instead of Rhino 5.

Open Rhino and run `verify_rhino.py`.
If this does not throw an error and prints the correct COMPAS version (`0.5.1`),
Rhino is properly configured.

> **Note**
>
> To run a script in Rhino, just type `RunPythonScript` at the Rhino command prompt
> and select the script you want to run.

**5. Configure your editor**

* Sublime Text 3: https://compas-dev.github.io/main/environments/sublimetext.html
* VS Code: https://compas-dev.github.io/main/environments/vscode.html

Finally, run `verify_editor.py` to check the setup.
If this prints `0.5.1` in the Terminal window, VS Code is properly configured.

## Examples

*   Plotters
    *   Shortest path (plot): [network_shortestpath.py](examples/network_shortestpath.py)
        <br />*Plot the shortest path between two vertices of a network.*
    *   Shortest path (interactive plot): [network_shortestpath.py](examples/network_shortestpath.py)
        <br />*Plot the shortest path between a given start vertex and a point picked by the user.*
    *   Equilibrium (dynamic plot): [network_equilibrium.py](examples/network_equilibrium.py)
        <br />*Plot the dynamic relaxation process of a network with randomly prescribed edge force densities.*
*   Rhino
    *   Subdivision: [mesh_subdivision_rhino.py](examples/mesh_subdividion_rhino.py)
        <br />*Generate a subdivision surface using a control mesh.*
    *   Mesh smoothing: [mesh_smoothing_rhino.py](examples/mesh_smoothing_rhino.py)
        <br />*Smooth a mesh on a given target surface.*
*   RPC
    *   Equilibrium: [rpc_fd_rhino.py](examples/rpc_fd_rhino.py)
        <br />*Force desnity calculation using Numpy/Scipy.*
    *   CDT: [rpc_cdt_rhino.py](examples/rpc_cdt_rhino.py)
        <br />*Constrained Delaunay Triangulation using triangle.*

## Troubleshooting

If you have a problem and don't find the solution here, please submit an issue on the issue tracker of the repository.

> **Problem**
> <br />*error: Microsoft Visual C++ 14.0 is required. Get it with "Microsoft Visual C++ Build Tools*

Follow the link to install Microsoft Visual C++ 14.0
https://www.scivision.co/python-windows-visual-c++-14-required/

> **Problem**
> <br />*Exception: The lib folder for IronPython does not exist in this location: C:\Users\AppData\Roaming\McNeel\Rhinoceros\6.0\Plug-ins\IronPython (814d908a-e25c-493d-97e9-ee3861957f49)\settings\lib*

This happens if you have a brand new installation of Rhino.
After opening Rhino and the PythonScriptEditor for the first time, the required folders will be created automatically.

> **Problem** 
> <br />*NoneType object has no attribute Geometry*

This sometimes happens in Rhino when wrapping Rhino Geometry.
Just reset the script engine and try again.

```
Tools > PythonScript > Edit > Tools > Reset Script Engine
```

> **Problem**
> <br />*I don't see the DisplayConduit in Rhino on Mac*

DisplayConduits are not supported yet on Mac. The result should be correct though...

