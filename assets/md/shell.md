# Shell Cheatsheet

### Shortcut
- `ctrl+c` - halts current command
- `ctrl+z` - stops current command
- `fg` - resume stopped command in foreground
- `bg` - resume stopped command in background
- `ctrl+a` - begin of line
- `ctrl+e` - end of line
- `ctrl+l` - clear screen
- `ctrl+w` - erases one word in current line
- `ctrl+u` - erases whole line
- `ctrl+r` - reverse lookup of previous commands
- `!!` - repeat last command
- `ctrl+d` - log out of current session
- `echo {a,b}.jpg` -expands to `echo a.jpg b.jpg`
- `echo {1..3}.jpg` -expands to `echo 1.jpg 2.jpg 3.jpg`


### Execution
- `nohup jupyter lab > /dev/null 2>&1 &` - redirect every output to nohup.txt


### Compression
- `tar zcvf file.tar.gz dir` - tar everything in dir and compress with gzip
- `tar zxvf file.tar.gz dir` - extract everything in file.tar.gz to dir with gzip
- `tar Jcvf file.tar.xz dir` - tar everything in dir and compress with xz
- `tar Jxvf file.tar.xz dir` - extract everything in file.tar.xz to dir with xz
- `gzip file` - compress file and rename to file.gz
- `gzip -d file.gz` - decompress file.gz
- `tar cf file.tar files` - tar files into file.tar
- `tar xf file.tar` - untar into current directory
- `tar tf file.tar` - show contents of archive
- tar flags:
    - `c` - create archive
    - `t` - table of contents
    - `x` - extract
    - `f` - specifies filename
    - `z` - use zip/gzip
    - `j` - bzip2 compression
    - `k` - do not overwrite
    - `T` - files from file
    - `w` - ask for confirmation
    - `v` - verbose


### Searching
- `grep pattern files` - search for pattern in files
- `grep -r pattern dir` - search recursively for pattern in dir
- `command | grep pattern` - search for for pattern in in the output of command
- `find . -name "*.js"` - find all file whose extension is js in current directory


### loop
- create 10 files
    ```
    for ((i=0; i<10; i++)); do
        touch test_$i.txt
    done
    ```


### xargs
- `find . -name "*.pyc"|xargs rm` - remove (rm) all file matching the pattern (filename *.pyc)
- `find . -name "pattern" | xargs rm -rf` - remove all file/dir matching the pattern
- `find . -name "*.c" -print0 | xargs -0 rm -rf` - correctly deal with filenames containing space
- `find . -name '*.sh' | xargs grep "SBATCH"` - find all occurence of "SBATCH" in files that match the pattern
- `echo a b c | xargs cmd` - execute `cmd 1; cmd 2; cmd 3`
- `echo a b c | xargs mkdir` - create three dir a b c
- Basics (c.f. [link](https://www.thegeekstuff.com/2013/12/xargs-examples/))
    - `xargs` - when you type xargs without any argument, it will prompt you to enter the input through stdin
    - `echo a b c | xargs -d\n` - specify delimiter using -d option
    - `echo a b c | xargs -n 2` - display only 2 items per line in the xargs output
    - `echo a b c | xargs -p -n 2` - prompt before execution
    - `xargs --show-limits` - display system limits on xargs


### Process Management
- `ps` - display currently active processes
- `ps aux` - ps with a lot of detail
- `ps uxf` - ps with tree view (only your process)
- `kill pid` - kill process with pid 'pid'
- `killall proc` - kill all processes named proc
- `bg` - lists stopped/background jobs, resume stopped job in the background
- `fg` - bring most recent job to foreground
- `fg n` - brings job n to foreground


### File
- `ls` - directory listing
- `ls -al` - formatted listing with hidden files
- `cd dir` - change directory to dir
- `cd` - change to home
- `pwd` - show current directory
- `readlink -f params.json` - show path of the file
- `mkdir dir` - create direcotry dir
- `rm file` - delete file
- `rm -rf dir` - remove directory dir
- `ln -s file link` - create symbolic link 'link' to file
- `touch file` - create or update file
- `cat > file` - place standard input into file
- `less file` - output the contents of the file
- `head file` - output first 10 lines of file
- `tail file` - output last 10 lines of file
- `tail -f file` - output contents of file as it grows
- `chmod octal file` - change permission of file
    - 4 - read (r)
    - 2 - write (w)
    - 1 - execute (x)
    - order: owner/group/world
- `chmod 777 files` - rwx for everyone
- `chmod 755 files` - rw for owner, rx for group/world

### ssh
- `ssh user@host` - connet to host as user
- `ssh -p port user@host` - connect using port p
- `ssh -D port user@host` - connect and use bind port


### Network
- `ping host` - ping host 'host'
- `whois domain` - get whois for domain
- `dig domain` - get DNS for domain
- `dig -x host` - reverse lookup host
- `wget file` - download file
- `wget -c file` - continue stopped download
- `wget -r url` - recursively download files from url
- `wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=FILEID' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=FILEID" -O FILENAME && rm -rf /tmp/cookies.txt` download gdrive files

### System Info
- `date` - show current date/time
- `cal` - show this month's calendar
- `uptime` - show uptime
- `w` - display who is online
- `whoami` - who are you logged in as
- `uname -a` - show kernel config
- `cat /proc/cpuinfo` - cpu info
- `top` - display Linux processes and cpu/mem usage
- `man command` - show manual for command
- `df` - show disk usage
- `du` - show directory space usage
- `du -h -d 1` - show direct subdirectory space usage
- `whereis app` - show possible locations of app
- `which app` - show which app will be run by default
