.. _crosscompile:

=======================================
Setup cross compile project with Eclipse
=======================================


Install Eclipse on Ubuntu 16.4
------------------------------

    - First download Eclipse from `Eclipse download <https://www.eclipse.org/downloads/>` and java if not already installed (default-jre)
        - Install a debugger, if not already installed *Eclipse IDE for C/C++ developers*.
        - Optional Install a *Remote System Explorer*
            - Help->Install New Software...-> --All Available Sites-- -> Mobile and Device Development or General Purpose Tools -> Remote System Explorer.

Build custom software development kit (sdk)
-------------------------------------------

    - source layers/openembedded-core/oe-init-build-env
    - bitbake console-hostmobility-dev-image -c populate_sdk
    - There will be a file output *angstrom-glibc-x86_64-armv7at2hf-neon-v2018.06-toolchain.sh* under deploy/sdk (file name can change over time and depend on target machine).
    - Run that script file and follow those instructions. 
    - Now there should be a sysroot folder, an environment setup file , an site-config and one version file under the install location. 
    - Run environment-setup-armv7at2hf-neon-angstrom-linux-gnueabi.sh before you start Eclipse to include the environment variables to your project.

Setup hello_word application
----------------------------

    - Create a new C or C++ project. Select Empty Project or Hello World template and Cross GCC toolchain.
    
    - Then, in the toolbar, click Project and select Properties from the drop down menu.
        - Navigate to *C/C++ Build --> Settings*

    - Within the Tool Settings tab, select [All configurations] from the configurations list. Select Cross GCC Compiler from the Tool Settings menu.
        - For Command, enter: **${CC}**

    - Under Cross GCC Compiler, select Miscellaneous.
        - For Other flags, enter: **${CFLAGS} -c**

    - Select Cross G++ Compiler from the Tool Settings menu.
        - For Command, enter: **${CXX}**

    - Under Cross G++ Compiler, select Miscellaneous.
        - For Other flags, enter: **${CXXFLAGS} -c**

    - Select Cross G++ Linker from the Tool Settings menu.
        - For Command, enter: **${CXX}**

    - Under Cross G++ Linker, select Miscellaneous.
        - For Linker flags, enter: **${LDFLAGS}**

    - Select Cross GCC Assembler from the Tool Settings menu.
        - For Command, enter: **${AS}**

    - Other environment variables can be found in the *environment-setup-armv7at2hf-neon-angstrom-linux-gnueabi* file.

    - For more information checkout `Toradex Guide <https://developer.toradex.com/getting-started/module-2-my-first-hello-world-in-c?som=apalis-imx6&board=apalis-evaluation-board>` 
    - and `Toradex Guide <https://developer.toradex.com/knowledge-base/linux-sdks>`.


Setup machine debugger
----------------------

    - First Run->Debug configurations...->c/c++ remote application->add (right click).
    - Change connection to your machine. 
        - ssh root@192.168.1.200 is default (eth0) for Mx4. 
        - Test it with browse and change path to where you want it to execute.
    - Under debugger->change main->gdb debugger to `arm-angstrom-linux-gnueabi-gdb`.
    - **tip** Add one debug and one Release (run configurations)



