Decompile a android apk, framework jar or a optimized odex apk compiled 
with user tag. 

Usage: decompile [options] <apk-file|jar-file|odex-file>

  -f <framewrok-odexs-dir>, --fodexs=<framework-odexs-dir>     
                        -- the base folder to look for the framework odex
                           files when decomile a odex apk or just the odex file.
                           Defaults to the PROGRAM_DIR/fodexs directory

  -h, --help            -- print this help and exit

Framework resources is formed in apk and code is formed in jar if not build
with user tag. The tool can decompile both of them.

When build with user tag, it will generate a small apk containing resources
and a odex file containing code. So this tool will decompile resources and
code if the argument is apk file, and just decompile code if argument is odex
file.

To decompile a odex file, it also needs a few of framework odex files. What
framework odex files needed depend on the odex apk you are decompiling. In
other words, different odex apk needs different framework odex files. The
most used framework odex files are android.policy.odex, bouncycastle.odex,
core.odex, pm.odex, core-junit.odex, ext.odex, services.odex, those you can
get from /system/framework/ in the device at which your odex apk is compiled
armed. The tool will give you tips when needed framework odex not fond.


Output:
  All files are saved in the directory named <apk> in current directory.

   src.jar                 -- source code formed in jar, open it with jd-gui
   src/                    -- source code formed in java
   res/                    -- resoures and so on
   AndroidManifest.xml     -- the android manifest file

Sample:
  1.
       decompile demo.apk 
  
  It will try to decompile resources and code whether it is built with user
  tag or not. Put demo.odex file in the same directory if it is built with
  user tag, or it just decompile resources.

  2.
       decompile -f odexs demo.apk 

  It is same as sample 1, except looking for framework odex files from the
  specified directory.

  3.
       decompile demo.odex 

  It will just decompile code, and looking for framework odex files from the
  default directory.

  4.
       decompile -f odexs demo.odex
  
  It is same as sample 3, except looking for framework odex files from the 
  specified directory.
  
  5.
      decompile framework-res.apk
  
  It will decompile framework resources.

  6.
      decompile framework.jar

  It will decompile framework code.

Author:
  Written by Richie Wang

Reporting bugs:
  Report decompile bugs to decompile4android@gmail.com

