![](img.png)

What is this?
-------------

GTKPass is a simple and minimal application which simply makes a small window with a textbox (for the password) and a combobox (for the user selection), at which you will have to type your password in and what not. When you then click "Sign In" it'll give a return status of either 0 or 1, meaning correct credentials or incorrect respectively.

GTKPass is not supposed to replace a display manager neither is it supposed to be a login prompt for everything it is simply a UI for the user to deal with. That is alone it does nothing more than provide a UI for [ispass](https://github.com/0neGal/ispass).

As an example a user could get their TTY to automatically Sign In, then execute `startx` which'll run your WM, and start the necessary apps, and at some point you'll run GTKPass, and if it returns 0, then start your keybindings daemon and the rest of the system, otherwise kill Xorg which will in turn result in the prompt reappearing...

As an example (this is taken from part of my startup script):

```bash
gtkpass && {
	sxhkd &
} || {
	killall Xorg
}
```

However my script doesn't actually support multi user logins, and currently GTKPass has no feedback on what user is being signed into, it simply checks if the password is right, in the future when I'm bothered and need it myself I'll make it output to `stdin`.

Dependencies
------------

 * [ispass](https://github.com/0neGal/ispass) by me
   - Used to verify the passwords of a user
 * [yad](https://github.com/v1cont/yad) by v1cont
   - Used to create the GTK UI with Shell scripting

yad, is available on a lot of repos, and ispass currently is only on my GitHub, however it's a simple `make install` to get it.

How to build?
-------------

`make install`

How to remove?
--------------

`make uninstall`
