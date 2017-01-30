# dialogue_enhanced
[Forum post](http://forums.wolfire.com/viewtopic.php?f=16&t=39819)  
## Howto use:  

1. Put folder in data/mods
2. Enable the mod in the File->Mods drop-down menu
3. Load levels/diagtest.xml in the mod's folder to see an example of its usage!

## What this adds:

* New `goto` command! Usage: `goto "foo"`, where "foo" is defined by @tag "foo"
* Also: You can check specific dialogue parameters for a variable. Example: `goto "foo" "bar" 1`, where goto will be ignored if script parameter "bar" is NOT 1.
* New `set_script_param` command! Usage: `set_script_param "param" "val"`, where param is the parameter and val is the value you want to set it to. Can set multiple params via `set_script_param "param1" "val1" ... "param4" "val4"`
* New `choice` command! Usage: `choice "choice1" "choice2" "choice3" "choice4"` - choice amount optional, limited at 4. To define a tag to where the choice will lead, do `@tag "choice1"`, `@tag "choice2"` etc.
* To make a choice, you have to press a number button from 1 to 4 that corresponds to the dialogue option.
* NOTE: The `@tag "string"` must match the choice string EXACTLY, CASE INCLUDED!
* New `end_dialogue` command, for when you want to end the dialogue prematurely! Useful with tags, though I'd reccomend doing the `@tag "end"` method instead (examplified below)

Example dialogue code:
```
say 2 "Guard" "Halt! You have broken the law. Pay fine or die."
say 1 "Turner" "..."
choice "Fight" "Die"
@tag "Fight"
say 1 "Turner" "I will fight!"
say 2 "Guard" "Welp. Guess we're fighting then."
send_level_message "make_all_aware"
goto "end"
@tag "Die"
say 1 "Turner" "i'll die instead"
say 2 "Guard" "oh ok"
send_character_message 1 ignite
send_level_message "make_all_aware"
goto "end"
@tag "end"
send_character_message 1 "set_dialogue_control false"
set_cam_control false
set_dialogue_visible false
```
Last tested and working on internal_testing branch
[Preorder the game here.](http://www.wolfire.com/overgrowth)
