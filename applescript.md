# only activate if no windows
tell application "Finder"
    activate
    if (count windows) is 0 then make new Finder window
end tell