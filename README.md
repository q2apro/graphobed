# graphobed #
vdi format size http://crysol.github.io/recipe/2015-11-17/vagrant-vdi-virtual-disk-for-virtualbox.html#.WS_4tBsrJEY


VAGRANTFILE_API_VERSION = "2"


HOME_DISK = "/var/home.vdi"

ddVagrant.configure(VAGRANTFILE_API_VERSION) do |config|
dd  config.vm.box = "deb/jessie-i386"

 dd config.vm.provider :virtualbox do |vb|
    if ARGV[0] == "up" && ! File.exist?(HOME_DISK)
      vb.customize ['createhd',
                    '--filename', HOME_DISK,
                    '--format', 'VDI',
                    '--size', 50000]

      vb.customize ['storageattach', :id,
                    '--storagectl', 'SCSI',
                    '--port', 0,
		    '--device', 0,
                    '--type', 'hdd',
		    '--medium', HOME_DISK]
    end
 
 
 end end
**graphobed** is a jquery script that finds equations on your website, 
parses them and embeds the according graphs below the formula as HTML5 canvas. 
To let the script find your equations, enclose them in `*# equation #*`

Embedded Graphs can be changed later on, using the created input field.
This script relies on: jquery, easeljs and math.js

@version 0.0.1

@date    2015-04-02

@license
Copyright (C) 2015 Kai Noack, http://www.echteinfach.tv/

Distributed under the terms of the MIT license.
http://www.opensource.org/licenses/mit-license.html


## USAGE: ##

Simply embed the script in your document's head section: 

    <script src="https://raw.githubusercontent.com/echteinfachtv/graphobed/master/graphobed.js" type="text/javascript"></script>

The formula parsing is done automatically.

## Screenshot and GIF-Demo ##

![](http://i.stack.imgur.com/a9EBD.png)

![](http://i.stack.imgur.com/IzSz3.gif)

We use the library in our [mathematics forum (see example here)](http://www.gute-mathe-fragen.de/223069/graphobed-eingegebene-formeln-automatisch-graphen-umgewandelt).

