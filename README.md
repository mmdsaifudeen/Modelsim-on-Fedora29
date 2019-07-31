# Modelsim-on-Fedora29

MODELSIM REQUIRES ITS SUPPORTED LIBRARY VERSIONS EXPLICITELY

Follow below steps for the updations!!

----------------DOWNLOAD AND KEEP THIS REPOSITORY-----------------

///////////////Downgrading fontconfig initially////////////////////////

rpm -e --nodeps fontconfig.i686
rpm -e --nodeps fontconfig.x86_64

rpm -i fontconfig-2.13.0-3.fc28.x86_64.rpm
rpm -i fontconfig-2.13.0-3.fc28.i686.rpm


///////////////////////////////////////////////////////////////////////////


////////////////  Downgrading libfreetype    //////////////////////////


++++++++++++++++Use compiled libraries or Compile yourself+++++++++++++++++++++



=============     Using readymade files here         ================


Copy Compiled freetype library to {{altera/13.1/modelsim_ase/lib32}} folder."lib32" folder is newly created for keeping library files.


============  Or   compile yourself using the link      =============

////////////////////////////////////////////////////////////////////////////////////


//////////////////////////////Update VSIM file//////////////////////////////////////


==============  Now Edit {{altera/13.1//modelsim_ase/bin/vsim}} file  ====================
                                              
-Rename <<<<   vco="linux_rh60"    >>>>>>>>  in the line 210 of <vsim> file to  <<<<<<<    vco="linux"  >>>>>.

-Below line 50 dir=`dirname "$arg0"`, add  
                                              export LD_LIBRARY_PATH=${dir}/lib
                                              
                                              
                                             
/////////////////////////////////////////////////////////////////////////////////////



/////////////////////////////  update .bashrc  in home folder of user  /////////////////

-  kwrite ~/.bashrc
-  Add following lines

          export PATH=$PATH:/home/user/altera/13.1/modelsim_ase/bin
          alias vsim="LD_PRELOAD=\"home/user/altera/13.1/modelsim_ase/lib32/libfreetype.so.6\" vsim"
          
          
//////////////////////////////////////////////////////////////////////////////////////////


//////////////////////////////  If poblem persist use this link to downgrade harfbuzz library //////////////////




////////////////////////   You will be greeted by modelsim GUI     ///////////////////////////////////








