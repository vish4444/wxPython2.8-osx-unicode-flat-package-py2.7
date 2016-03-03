# wxPython2.8-osx-unicode-flat-package-py2.7
How to fix WXPython Issues in OS X Terminal

  - Due to wxpython runs only on 32bit architecture in OS X and most of the installer failed to install it in OS X, I created a re-package version of wxpython to solved the issue. 

  Here are the steps.  

  - Download the wxpython version of your choice (e.g. wxPython2.8-osx-unicode-2.8.12.1-universal-py2.7.dmg) 
  - Mount the dmg file.     
  - hdiutil mount wxPython2.8-osx-unicode-2.8.12.1-universal-py2.7.dmg 
  - Copy the pkg folder to working_directory     
  - mkdir ~/working_directory     
  - cp -r  /Volumes/wxPython2.8-osx-unicode-2.8.12.1-universal-py2.7/wxPython2.8-osx-unicode-universal-py2.7.pkg ~/working_directory 
  - Create package_root folder and extract pax.gz file     
  - mkdir ~/package_root     
  - cd ~/package_root     
  - pax -f ~/working_directory/wxPython2.8-osx-unicode-universal-py2.7.pkg/Contents/Resources/wxPython2.8-osx-unicode-universal-py2.7.pax.gz -z -r 
  - Create scripts folder and rename the bundle’s preflight/postflight scripts to preinstall/postinstall scripts.     
  - mkdir ~/scripts     
  - cd ~/working_directory/wxPython2.8-osx-unicode-universal-py2.7.pkg/Contents/Resources/     
  - cp preflight ~/scripts/preinstall     
  - cp postflight ~scripts/postinstall - Create flat package using pkgbuild     
  - cd ~/working_directory     
  - pkgbuild —root ~/package_root —scripts ~/scripts —identifier com.wxwidgets.wxpython wxPython2.8-osx-unicode-flat-package-py2.7.pkg 
  - Now Install the new wxPython package     
  - sudo installer -pkg ~/working_directory/wxPython2.8-osx-unicode-flat-package-py2.7.pkg -target / 
  - Viola!
