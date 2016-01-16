# *nix Scavenger Hunt

Complete the following challenges using the command-line interface on your favorite
Unix or Linux operating system. You are welcome and encouraged to consult any
additional documentation online or in books.

Please add your answers/responses/text pastes to the document after each prompt.

Note: For some of the challenges you will need to reference files included with
this repository, so you will need to fork the repo into your own Github account
and then clone it to your development environment.

## The Challenges

### Navigating the Filesystem

* Get an idea of where you are in the operating system. Use the `pwd` command to find your "path to working directory"--your current location in the filesystem of your devbox. *Paste the output of the `pwd` command here:*

/home/cabox/workspace                                                                                                                          

* Discover more about this filesystem. Use `ls` (the "list" command)to see what is in this directory. *What directories and files do you see when you run `ls`?*

LICENSE  README.md  challenge_files  nix_scavenger_hunt.md  nix_scavenger_hunt_stretch.md                                                      

* You can use *options* to modify how a command runs. Try using `ls -alh` to see the contents of your current directory. *How are the results different when you use the `-alh` options?*

It seems as though using -alh gives us the individual file sizes, total file size and the time the files were created in EST

* The `man` ("manual") command tells you more about how any given command works. (*WARNING:* CodeAnywhere does not support the man command. You can click the following link to complete this task: http://linux.die.net/man/)Run `man` to see instructions about how to use `man`. Then use `man` to learn what the `a`, `l`, and `h` options mean when used with the `ls` command. *Write down what those options do?*

a- lists all files including ones that begin with a dot
l- means use a long listing format
h- human readable

* Commands can also take *arguments*, which are usually the names of files or locations that you want the command to work with. Try running `ls /` to see what files are in the *root* directory of the filesystem. *What files and directories do you see listed?*

bin  boot  dev  etc  fastboot  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var                               

* A Unix filesystem has a few special shortcuts to refer to specific locations. `/` indicates the *root* of the filesystem, meaning the top-most directory in the filesystem hierarchy. Use the `cd` ("change directory") command to move to the root directory. (Hint: Use `man` to look up the `cd` command if you have any issues) *Then run `pwd` and paste the output here:*

/                                                                                                                                    

* Another special shortcut in Unix is the `~` location. This indicates the *user root* directory, meaning the top-most directory in the hierarchy that comes below your user account. Use `cd` to move to `~`. *Run `pwd` and paste the response here:*

/home/cabox                                                                                                                                    

* Change directory into the `challenge_files` directory. Use `ls` to find only the files with a `.demo` pattern. *How many files do you find?*

2015_special_stuff.demo  cloaked-wookie.demo  scooter-double-mamba.demo                                                                        

* Use the `cd` command to move "up" one directory. *Where are you in the filesystem now?*

/home/cabox/workspace                                                                                                                          

* Press the up arrow a few more times. *What do you see?*

It automatically added the last command which was pwd

* Run the `history` command. *What do you see?*

    1  pwd                                                                                                                                     
    2  ls                                                                                                                                      
    3  ls -alh                                                                                                                                 
    4  ls/                                                                                                                                     
    5  ls /                                                                                                                                    
    6  cd /                                                                                                                                    
    7  pwd                                                                                                                                     
    8  cd                                                                                                                                      
    9  pwd                                                                                                                                     
   10  cd challenge_files                                                                                                                      
etc etc... a full detailed list of every command that I submitted

### Observing the System

* Discover what account you are logged into using the `whoami` command. *What username are you currently using?*

cabox

* How long has your system been running? Use `uptime` to see, and *paste the result here:*

cabox    pts/0        Jan 12 20:30 (54.186.244.104)                                                                                            

It does not appear that anyone else is using my system.  It is only displaying cabox for a user.

* Run `ps aux` and review the results. (Hint: Use `man` to learn more about the `ps` command and options.) *How do you interpret what you see here?*

ps displays information about a selection of the active processes
a- causes ps to list all options within the terminal
u- displays in user-oriented formatting
x- causes ps to list all processes owned by you

* Run `top` and review the results. (Hint: You may need to use `ctrl-c` to get out of this app.) *How do you interpret what you see here?*

This shows the system running in real-time.  

### Finding and Viewing Files

* Make sure you are in the `challenge_files` directory. Use the `*` wildcard to find all the files that have the word "credit" in the filename. *How many files did you find?*

2

* Use the `more` command to view one of the `credit_cards` files you just discovered. (Hint: Type `q` to quit viewing the file. Press the `spacebar` to page down. Use your keyboard arrows to move up/down.) *What is the date in the file you have viewed?*

Last updated: 01-15-2015                                                                                                                       

* Use the `find` command to search for files more effectively. Search the sub-directories under `challenge_files` to find the location of the file named `modi_laboriosam.txt`. *Where is that file located?*

./tmp/modi_laboriosam.txt                                                                                                                      

* Use the `grep` command to search for text within a file. Use `grep` on all the `.user` files in `challenge_files` to find which files contain "WA" (the abbreviation for Washington state). *How many files did you find?*

2

* Use the `-r` option of `grep` to *recursively* find the text "Waldo" hidden in a file somewhere under the `challenge_files` directory. *Paste the result showing the file and line where the word "Waldo" shows up.*

serial-numbers/eaque_molestiae.txt:Ut est maiores quia autem. Nisi modi Waldo sed corporis sit explicabo ut est. Et est placeat ea sunt sunt co
nsectetur sunt incidunt. Explicabo vel esse blanditiis dolorem culpa non quia.  

### Pipes and Connecting Commands

* Sometimes it's useful to output the results of a command to a text file for further analysis, reference, or processing. Try running `ls > files.txt`. Notice that the file `files.txt` was created. View that file using `more`. *What do you see in the `files.txt` file?*

It seems to contain a list of users

* Notice that if you run `ls -alh` in the `challenge_files` directory, the files scroll by very quickly. Sometimes it would be better to get the results in a paginated format. Try running `ls -alh | more`. *Describe what you see when you run `ls -alh | more`.*

This shows a breakdown of each users activity including the date as well as size of each change

* Earlier, when you viewed the list of active processes on your devbox using `ps aux`, the list was probably really long. You can make this list more manageable by using the pipe (`|`) to filter the results of `ps` using `grep`. Run `ps aux | grep <your_username>` to see what processes are running for your specific user. *Paste the list of processes that reference your username here:*

cabox      545  0.0  0.2  64012  1488 ?        S    14:03   0:00 sshd: cabox@pts/0                                                             
cabox      546  0.0  0.3  18144  2068 pts/0    Ss   14:03   0:00 -bash                                                                         
root       569  0.0  0.6  63876  3344 ?        Ss   15:16   0:00 sshd: cabox [priv]                                                            
cabox      571  0.0  0.2  64012  1504 ?        S    15:16   0:00 sshd: cabox@notty                                                             
cabox      572  0.0  0.1  12920   996 ?        Ss   15:16   0:00 /usr/lib/openssh/sftp-server                                                  
cabox      585  0.0  0.2  15520  1144 pts/0    R+   15:26   0:00 ps aux                                                                        
cabox      586  0.0  0.1   8816   764 pts/0    S+   15:26   0:00 grep --color=auto cabox 


