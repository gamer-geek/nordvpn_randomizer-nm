# nordvpn_randomizer-nm  (Network-Manager Edition)

**Note**, this was written while bored and drunk mainly on my cell phone so the code is crude, but working just fine. I will improve when time allows for it. Better usage/installation instructions included.

This Bash script was created for simply randomize the available [NordVPN](https://nordvpn.com/) OpenVPN UDP files for a specific country choosen by the user. This script is also provided AS-IS and is a work in progress when I have some time over.

It assumes you have followed the [instructions](https://nordvpn.com/tutorials/linux/openvpn/) for the shell installation method. What that page doesn't add is that you can create a file named *auth.txt*  in */etc/openvpn/* (as root) and use it for bit of automation regarding connecting to the VPNs provided by NordVPN.

```
$> sudo nano /etc/openvpn/auth.txt
```

- Now add your NordVPN **username** on the first row and your NordVPN **password** on the second row.

- Save and exit nano by pressing X and confirm.

```
$> sudo chmod 0600 /etc/openvpn/auth.txt
```

The problem now is that each NordVPN OpenVPN UDP files provided doesn't understand that is should use the file you just created. However, this script takes care of that automagically so you don't have to worry about it.


Let's clone this puppy to your workstation/server.

```
$> mkdir ~/sources && cd ~/sources

$> git clone https://github.com/damianrath/nordvpn_randomizer-nm.git
```

Now just put a symbolic link to *~/sources/nordvpn_randomizer-nm/nordvpn_randomizer-nm* somewhere in your path. Preferably in *~/bin/*.


After you have run the script (as root) it will provide you with a menu of options. Here you can add and remove a randomized VPN. When you add a VPN it will ask you for a country-code. If you don't know which country-codes that are available you can just press ENTER and a list will be provided for you. Afterwards it will add a randomized VPN to your Network-Manager (GUI), based on your country selection, where you can select to start/stop it like normal.

When you want to get a new randomized VPN you just start this script again and use the second option on the menu. It will check if the VPN in question is started and stop it if necessary. After that it will remove it from the Network-Manager list. When that's done you can just choose the first option on the menu and the script will provide you with a new randomized VPN.

That's it!



## TODO

- Clean up the script. Drunk coding ftw.
- Add some more features.
- Add more error checking for the shellscript-challenged people.



## Disclaimer

I'm not affiliated with NordVPN in any way except being a normal customer that enjoys their services.
