Following files are modified:
utils_tool.py
data_provider.py
eval.py

For CPP file errors such as the following:
- tensorflow_PSENet-master/pse/pse.so: undefined symbol: _Py_ZeroStruct #48 
- python37.lib(python37.dll) : fatal error LNK1112: module machine type 'x64' conflicts with target machine type 'x86'

Solution for Ubuntu machine:
1.
   (i) delete pse.so file
  (ii) change the Makefile (saved here)
 (iii) run the eval.py file
 
 2. Do the following change in the Makefile:
    python-config --> python3-config


Solution for Windows machine:

1. Download Developer Command Prompt for VS

https://visualstudio.microsoft.com/downloads/ --> Tools for Visual Studio 2019 --> Build Tools for Visual Studio 2019

2. Run this .bat file from the VS cmd prompt (to set x64 env):

"C:\Program Files (x86)\Microsoft Visual Studio\2019\BuildTools\VC\Auxiliary\Build\vcvars64.bat"

3. comment line 8 and 9 from "tensorflow_PSENet-master\pse\__init__.py" file.

4. Run the following to get the executable:

cl pse.cpp /I ./include /I "C:\Users\A1031613\AppData\Local\Continuum\anaconda3\include" /LD /Fe:pse.pyd /link/LIBPATH:"C:\Users\A1031613\AppData\Local\Continuum\anaconda3\libs"

5. Run the eval file 
