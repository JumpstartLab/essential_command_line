## Core Question

"What are the essential tools / understandings that a developer needs to have to make effective use of the Linux/MacOS command line?"

### Background

* understanding of the "unix philosophy" of small commands
* understanding of unix processes

### The Environment

* understanding basic bash
* environment variables
* aliases
* file system
  * /usr/local
  * /home
  * /var
  * /etc
* file modes/permissions

### Commonalities

* standard command-line-switches paradigm (-v, --help, etc)
* how services are accessible on ports (http, ssh)

### Basic Tools

* ls
	* List the contents of a directory
	* you can control sort order and display format and color using switches
	* detailed (long) listing: `ls -l`
	* show "hidden" files with `ls -a`
	* listing will be recursive with `ls -R`
* cp and mv
	* `cp file1 file2` - make a copy
	* `mv file1 file2` - "move" the file
* rm
	* Delete a file or directory
	* `rm -i file*` will prompt before each removal
	* use `rmdir` or `rm -r` to remove a directory and everything under it
* less
	* View a file
	* `less` is a "pager", allowing for a memory-friendly way of viewing even large files
	* `space` to scroll forward one page; `b` to go back on page
	* `/` to search forward, `?` to search backward
* sudo
	* Run a command as another user - but only if you have permission
	* users can be allowed to run certain commands, and as certain users
	* most often used to allow a regular user to run a command as root
	* `less /var/log/messages` => `Permission denied`
	* `sudo less /var/log/messages` => after typing password, log file is displayed
* ssh
	* Securely connect to another host
	* `ssh user@host`
	* authentication is via password or public-key
	* run a remote command: `ssh user@host ls -l /tmp`
* telnet
  	* _Insecurely_ connect to another host
	* Not encrypted like ssh, plain text
	* `telnet www.example.com 80`
* scp
	* Copy a file to/from another host
	* `scp file1 user@host:/tmp`
	* the same ssh rules apply
* man
	* Get help (a manual) for unix commands
	* `man ssh`
	* also try command --help
* grep
	* Find regular expression matches in a file
	* `grep Load log/development.log`
	* use `-i` to ignore case
	* use `-c` to just count matching lines
	* recurse entire directories: `grep -r Controller app`
* tar
	* combine and compress files together for archive or transfer
	* create: `tar cf important_files.tar a.txt b.txt c.csv`
	* list contents: `tar tf important_files.txt`
	* extract: `tar xf important_files.tar`
	* use -z to compress or uncompress using gzip:
		* `tar zcf important_files.tar a.txt b.txt c.csv`
		* `tar zxf important_files.tar`
* head and tail
	* show the beginning or the end of a file
	* `head -5 file` will show the first 5 lines
	* `tail -15 file` will show the last 15 lines
	* special case to "watch" a file as it is appended to: `tail -f file`
* basic services and daemons, and where their configuration files live

### Advanced Tools

* find
* ps
* top
* curl
* lsof
* awk/sed

### Techniques

* quickly editing files with vi
* simple shell scripting
* "piping" one command to another
	* tail -f logfile | grep -i error
	* grep ^Started development.log | awk -i '{print $3}'
* knowledge of regular expressions
* ability to (at least) read bash, perl, python code 
* git or svn command-line interface
* how to launch your gui tools from the command-line