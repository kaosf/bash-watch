# Bash Watch

Watch current directory's filesystem events **create**, **delete**, **modify**
and **move**.

On emitting those events, execute specified commands or syncronize current
directory with another remote machine by `rsync` command.

## Prerequisites

`inotifywait` command is needed.

Run
`sudo apt-get install inotify-tools`,
`sudo yum install inotify-tools`
or etc.

`rsync` command in `watchb-rsync` requires SSH connection with a remote machine,
so SSH public key should be registered in it.

## Usage

```bash
./watchb 'ls && date'
```

You can specify excluding file regexp.

```bash`
./watchb rake 'log\/.*\.log'
```

`rake` command runs on modifying current directory, but all `log/*.log`
modifications are ignored.

You can escape from the infinite loop like following;

Run `rake` -> `log/test.log` is modified ->
Run `rake` -> `log/test.log` is modified -> ...

```bash
./watchb-rsync yourhost.net
./watchb-rsync yourhost.net some/where/from/home
./watchb-rsync yourhost.net some/where/from/home username
```

`watchb-rsync`'s 2nd argument *dst-path* is defaultly the same to local current directory path. (e.g. `cd ~/some/where && watchb-rsync yourhost.net` is same to `cd ~/some/where && watchb-rsync yourhost.net some/where`.)

3 (or 2) arguments are used for `rsync` as;

```bash
rsync -avz -e ssh --delete ./ ${3}@${1}:${2}
# or
rsync -avz -e ssh --delete ./ ${1}:${2}
```

## References

* http://stackoverflow.com/questions/6475252/bash-script-watch-folder-execute-command
* http://superuser.com/questions/181517/how-to-execute-a-command-whenever-a-file-changes
* http://stackoverflow.com/questions/2972765/linux-script-that-monitors-file-changes-within-folders-like-autospec-does
* https://github.com/rvoicilas/inotify-tools/wiki
* http://www.usupi.org/sysad/157.html
* http://labs.crooz.co.jp/archives/62

## License

[MIT](http://opensource.org/licenses/MIT)

Copyright © 2014 ka
