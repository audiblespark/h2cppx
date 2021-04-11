h2cppx(vim-port): Parse C++ header files and generate C++ implementation code 
===========================================================================
**Purpose:** Parse the C++ header file and generate C++ implementation code

**Required:** Python 3.x

**Author:** xiaok

**External modules required:** cheetah3 yaml(python package)

**Third-party(the plugin already include):** pyvisitor CppHeaderParser(modification) 

[Github-Link](https://github.com/xuqix/h2cppx.git)

Installation
------------
Before start, make sure you have installed the python package "yaml",
Then run below command:

    pip install cheetah3 yaml

Use your favorite plugin manager to install it.

Vim plug:

`Plug 'keeneared/h2cppx-vim'` to ~/.vimrc and install it,then:

Mapping example:

    e.g:
    nmap <F3>  :H2cppx<ESC>
    nmap <F4>  :H2cppxLine<ESC>
    nmap <F3>p :CpH2cppx<ESC>
    nmap <F4>p :CpH2cppxLine<ESC>
    nmap <F5>  :H2cppxAuto<ESC>

Config
------
If the plugin can't find the python path in your computer,
you need set "g:python_path" in the .vimrc file:

    let g:h2cppx_python_path = '/usr/bin/python'

and you can specify the .cpp file name extension like this:
(default value is 'cpp')

    let g:h2cppx_postfix = 'cxx'

Five code-generate template file are provided by default, 
you can configure them in '.vimrc' like this(template0-4,default is template1):

    let g:h2cppx_template = 'template4' 

If needed, you can refer to the default template and write your own template
files. Use the absolute path to configure it :

    let g:h2cppx_template = '/home/xxx/.../xxx'

Finally, you can add a configuration file `.h2cppx_conf` in your project 
directory to help the plugin search for a .cpp file. Otherwise the plugin will use
.cpp file in your header file directory.
The configuration file might look like:
    
    /home/test/temp/src
    src1
    src2

See the project_sample directory.

Usage
-----
The plugin function description:

* :H2cppx  
  Parse the C++ header file and generate .cpp file with the same name

* :CpH2cppx  
  Store file content in the register instead of creating a file. Paste with "p".

* :H2cppxLine  
  Generate C++ code of the line under the cursor, and append it at the end of the .cpp file.

* :CpH2cppxLine  
  Generate C++ code of the line under the cursor and store it in a register. Paste with "p". 

* :H2cppxAuto  (Recommended)   
  Auto Contrast header and implementation files. Find
  function declarations in the header file and append
  the newly added to the implementation file. If the 
  file does not exist a new file is created!

