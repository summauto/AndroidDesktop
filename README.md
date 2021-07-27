# AndroidDesktop
Turning my Samsung S21 Ultra into my Desktop

1. Follow [this code](https://github.com/tuanpham-dev/termux-ubuntu)
2. 

## chrome
1. I set "request desktop site" under chrome://flags". What im thinking is that i shd set my phone screen to a low resolution then my Dex resolution to high. So that it'll default to desktop site on Dex only.

## Running a terminal in android
### termux
1. uses proot, doesn't need root access to the phone so banking apps are not affected.
2. Can i get the same accessibility as ubuntu with termux? 
3. Try directly using termux, and just xfce4 as a UI.
    1. <mark>https://wiki.termux.com/wiki/Graphical_Environment</mark>
4. `pkg update` doesn't work, I get 403 Forbidden. This is because the sources are down.
	1. [They](https://github.com/termux/termux-packages/issues/4358) say just add to the ignore list and carry on.
	2. Repo for `game-packages-24` and `science-packages-24` are down.
		1. They are recommending to change repo with `termux-change-repo`. (Use your mouse to select, not the arrow keys)
			2. **I selected the albatross mirror and it works**

### Ubuntu + xfce4 (via VNC)
3. Tried to run an Ubuntu GUI on it, keeps crashing
	1. [try to get the logs](https://wiki.termux.com/wiki/Recover_a_broken_environment)
    2. [could it be proot's problem?](https://github.com/termux/proot/issues/46)
    3. [another proot issue](https://github.com/termux/proot/issues/139) 

```saved these links for viewing another time. gotta go work now```

## Best Remote Desktop Solution
1. but how do I prevent the com from not loading graphics when the lid is closed (or headless)?
    1. this affects solidworks and fusion360, but youtube is ok?
    2. https://knowledge.civilgeo.com/knowledge-base/enabling-gpu-rendering-for-microsoft-remote-desktop/ ← this is telling me to enable GPU rendering for remote desktop.
        1. Oops can’t find ˋgpedit.mscˋ
            1. https://www.itechtics.com/enable-gpedit-windows-10-home/ 
            2. There is no Local Group Policy Editor for Windows 10 Home. Use regedit instead.
            3. No, use ˋmmcˋ > `IP Security Policies on Local Computerˋ
            4. **I am able to access group policy with Policy Plus**
        2. Enabled "Use hardware default graphics adapter for all Remote 
            1. **IT WORKS!**
        3. Followed [these](https://knowledge.civilgeo.com/knowledge-base/enabling-gpu-rendering-for-microsoft-remote-desktop/) steps.
### Remote Desktop Protocol (RDP) - Microsoft Remote Desktop
1. also has a client-server protocol
2. Remote Desktop Manager is only a client UI to help you log in to several servers at once (and manage them)
3. Does this allow key mappings? Vnc, teamviewer all don’t, but I rmb “Remote desktop connection” did allow that.
	1. You just do the mapping on Windows itself (using PowerToys > Keyboard Manager). Currently i've mapped these:
		1. Alt+1 --> Alt+Tab
		2. Alt+4 --> Alt+F4
		3. Shift+W --> Win

### Teamviewer still in the lead
1. Also, i can’t use keyboard shortcuts here. They keep sending them to the android environment. Online asks me to set it in “Actions”, but this tab only exists for native desktop clients. This Dex only has the limited android menu.
2. **By setting Teamviewer to “Start Teamviewer with Windows” and “Grant easy access”, I can restart my server computer and straight away gain remote access!**
3. However, vulnerable to exploits. https://www.secpod.com/blog/high-risk-vulnerability-in-teamviewer-could-be-exploited-to-crack-users-password/ 
    1. This guy say its better to use native rather than 3rd-party 

### Chrome Remote Desktop
1. Actually works quite well out of the box.
2. Still no key mappings - not for the android site. The windows/mac one is able to key map in Fullscreen mode.

### TigerVNC Server + bVNC Client
1. TigerVNC uses Tight VNC encoding
2. This is better cos both are open-source!
3. However, the VNC protocol is slower than RDP and the proprietary protocol teamviewer uses.
4. Need to check the cybersecurity implications of this.
    
