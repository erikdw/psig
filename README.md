# psig
Print linux process signal information.

## Set up:
```
curl -O https://raw.githubusercontent.com/erikdw/psig/master/psig
chmod +x psig
```

## Usage:
```
# Print signal info for a specific PID
./psig -p <PID>

# Print signal info for all PIDs
./psig -a

# Print blocked signals for a specific PID
./psig -p <PID> -b

# See other options:
./psig -h

```

## [Taco Bell Programming](http://widgetsandshit.com/teddziuba/2010/10/taco-bell-programming.html) Examples:
```
# Print caught signals from all threads (subtasks) of a specific PID
ls -d /proc/<PID>/task/[0-9]* | cut -d/ -f5 | xargs -I{} ./psig -c -p {}

# Print ignored signals from all 'processname' processes (using [] trick to prevent inclusion of grep process)
ps aux | grep processnam[e] | awk '{print $2}' | xargs -I{} ./psig -s -p {}
```
