---
title: peeps
layout: default
---

# Configuring a Chromebook ===

 1. back up your data
   * you may need to upgrade your browser to acquire the backup software through Google
   * download and install the Chromebook recovery software from the Chrome store
   * open the app to create a recovery drive
 2. Enable developer mode
   * Press Esc+Refresh keys and push power button
   * If first time in developer mode, press Ctrl+D and enter through the warning screens
   * Process will clear the local disk, and should take about 15-25 minutes to clear all data
 3. Download the latest crouton version from this [[https://goo.gl/fd3zc |link]]
 4. Enter terminal from the Chromebook
   * press Alt+Ctrl+t
   * open shell with command:
    shell
    
 5. Install Ubuntu with chosen environment
     sudo sh ~/Downloads/crouton -t name_of_environment //name can be 'kde', 'xfce', etc.
 6. open the shell with: 
    sudo startenv //startenv can be 'startkde', 'startxfce', etc.
 7.set up your ubuntu environment and update packages needed accordingly
 8. Recommended setup:
    sudo apt-get update
    sudo apt-get install ssh
 9. At this point, you are able to use ssh from the chromebook in the environment you have installed these in. You can run ssh by typing:
    ssh -X username@host.address
 10. Press to cache the register address.
