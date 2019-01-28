#
# UNIX cheatsheet
#

# Who is listening on a given TCP port on Mac OS X?

lsof -nP -i4TCP:3000 | grep LISTEN

# Send certain signal to process

kill -SIGINT 72859

# Print list of signal names

kill -l