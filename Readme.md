Awesome:


##############
How to add custom command:

.config/awesome/rc.lua

-- {{{ Key bindings
globalkeys = gears.table.join(
    -- My Bindings
    awful.key({ modkey,           }, "v", function () awful.util.spawn_with_shell("subl -n -a /home/simha/.public_html/.vlist") end),
    awful.key({ modkey,           }, "e", function () awful.util.spawn_with_shell("pcmanfm") end),
    awful.key({ modkey,           }, "l", function () awful.util.spawn_with_shell("sleep 1 && xset dpms force off; slock") end),
    awful.key({ modkey,           }, "s", function () awful.util.spawn_with_shell("slock systemctl suspend -i") end),

#############
change menu and add screen brightness less and reset

editor = "subl -a -n"
editor_cmd = terminal .. " -e " .. editor

-- {{{ Menu
-- Create a launcher widget and a main menu
myawesomemenu = {
   { "hotkeys", function() hotkeys_popup.show_help(nil, awful.screen.focused()) end },
   { "manual", terminal .. " -e man awesome" },
   { "edit config", "subl -n -a" .. " " .. awesome.conffile },
   { "restart", awesome.restart },
   { "quit", function() awesome.quit() end },
}

bright = {
  { "inc","xcalib -contrast 80 -alter"},
  { "dec","xcalib -contrast 80 -alter"},
  { "clr", "xcalib -c"}
}

mymainmenu = awful.menu({ items = { { "awesome", myawesomemenu, beautiful.awesome_icon },
                                    { "open terminal", terminal },
                                    { "bright", bright}
                                  }
                        })

mylauncher = awful.widget.launcher({ image = beautiful.awesome_icon,
                                     menu = mymainmenu })

-- Menubar configuration
menubar.utils.terminal = terminal -- Set the terminal for applications that require it
-- }}}

###################
rezise window -- mod + right
move -- mod + left

