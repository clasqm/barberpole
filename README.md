# barberpole v.0.1
by Michel Clasquin-Johnson

Displays a barberpole with an explanatory message.

![barberpole](barberpole.png)

This application uses the spinner library developed by Jim Saxton (bbjimmy)

SECTION 1: For use in bash or any language that can shell out to bash:

Usage: barberpole <parameters> <--msg=message>

PARAMETERS

All parameters are case-sensitive, i.e. they must be entered in lowercase.

By default, the barberpole displays in the exact centre of the screen. To change that, use the following parameters:
    --tl    --topleft       Display in top left corner
    --tr    --topright      Display in top right corner
    --bl    --bottomleft    Display in bottom left corner
    --br    --bottomright   Display in bottom right corner
    --al    --alert         Display  a position ¾ from the bottom of the
							screen, roughly where Haiku posts its alerts.

The barberpole will actually appear in the screen centre and immediately be moved to the new location, but unless you have incredibly old hardware and the eyes of a dragonfly, you are unlikely to notice.

    --rv    --reverse       reverse direction of barberpole's movement.
    
    --msg=Text of the explanatory message
        Default: Please Wait ...
        This MUST be the last parameter supplied. No spaces around the =.
        Everything that comes after "--msg=" will be displayed. You do not need
              to surround this text with quotes. In fact, if you need to display either a 
              single or a double quote you will need to escape them:

              barberpole --msg=The cat\'s in the cradle
              barberpole --msg=This so-called \"computer\" thing is just a craze.

              If your text is too long, it will simply be truncated at BOTH ends.
              


When you no longer want to display the barberpole, you can remove it in two ways:

    hey barberpole quit
    kill barberpole

I recommend you use the first method. it gives an error message, but it does work

======================================================

SECTION 2: Special features for yab programmers
The following (case sensitive) yab commands will change the appearance and behaviour of the barberpole on the fly from within your yab program. You can use "Message Send" or "MESSAGE SEND" if you prefer, but the specifier "application/x-vnd.barberpole" and what follows it MUST be in lowercase

Another way to exit the barberpole (three of them, actually):
a = message send "application/x-vnd.barberpole", "done"
a = message send "application/x-vnd.barberpole", "quit"
a = message send "application/x-vnd.barberpole", "exit"

Changing the explanatory text label beneath the barberpole:
a = message send "application/x-vnd.barberpole", "newmsg:The new message comes here"

Note that quotation marks must be escaped TWICE when you change it from inside a yab program:
a = message send "application/x-vnd.barberpole", "newmsg:The cat\\'s in the cradle"

The following four commands will send the barberpole 50 pixels in the given direction. However, the barberpole will never move beyond the edge of the screen.
a=message send "application/x-vnd.barberpole", "right50"
a=message send "application/x-vnd.barberpole", "left50"
a=message send "application/x-vnd.barberpole", "up50"
a=message send "application/x-vnd.barberpole", "down50"

The following four commands will send the barberpole to a given screen corner:
a=message send "application/x-vnd.barberpole", "topleft"
a=message send "application/x-vnd.barberpole", "topright"
a=message send "application/x-vnd.barberpole", "bottomleft"
a=message send "application/x-vnd.barberpole", "bottomright"

The following command will send the barberpole to a position ¾ from the bottom of the screen, roughly where Haiku posts its alerts:
a=message send "application/x-vnd.barberpole", "alert"

These commands can be combined with the bash commandline parameters. The following yab sequence creates a barberpole with a custom message in the top left corner, then moves it down and to the right by fifty pixels.

system("barberpole --tl --msg=The cat\\'s in the cradle &")
sleep 0.1
a=message send "application/x-vnd.barberpole", "right50"
a=message send "application/x-vnd.barberpole", "down50"


a = message send "application/x-vnd.barberpole", "reverse"
reverses the direction of movement in the barberpole. You can undo this with
a = message send "application/x-vnd.barberpole", "normal"
 
Display an About box
a = message send "application/x-vnd.barberpole", "about"

FAQ: 

Q: What happens if two apps call barberpole simultaneously and my yab app tries to modify one of them?
A: barberpole is set up as a single-instance app to avoid this situation. The second app that tries to call up a barberpole will get an error and do nothing.

Get it here: https://github.com/clasqm/barberpole

Binaries: https://sourceforge.net/p/barberpole/


