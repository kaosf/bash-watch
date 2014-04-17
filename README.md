# Bash Watch

Watch current directory's filesystem events **create**, **delete**, **modify**
and **move**.

On emitting their events, execute specified commands or syncronize current
directory with another remote machine by `rsync` command.

## Prerequisites

`inotifywait` command is needed.

Run
`sudo apt-get install inotify-tools`,
`sudo yum install inotify-tools`
or etc.

## Usage

```bash
./watchb 'ls && date'

./watchb-rsync yourhost.net
./watchb-rsync yourhost.net some/where/from/home
./watchb-rsync yourhost.net some/where/from/home username
```

## References

* http://stackoverflow.com/questions/6475252/bash-script-watch-folder-execute-command
* http://superuser.com/questions/181517/how-to-execute-a-command-whenever-a-file-changes
* http://stackoverflow.com/questions/2972765/linux-script-that-monitors-file-changes-within-folders-like-autospec-does
* https://github.com/rvoicilas/inotify-tools/wiki
* http://www.usupi.org/sysad/157.html

## License

[MIT](http://opensource.org/licenses/MIT)

Copyright © 2014 ka
