# Linux Processes
this notes will include commands about ps, top, htop, atop and more. 

- `top command` - this display information about linux processes
- `atop command` - this display advance system and process monitor
- `htop command` - this is an interactive process in linux
- `pgrep command` - this is a look up or signal processes based on name and other attributes
- `pstree command` - this shows a tree of processes
- `btop command` - this is a new command for linux, and used for resource monitor CLI just like task manager
- `glances command` - this displays a comprehensive linux processes

---

### What is TTYS?
TTYS or Teletypewriter is a way of communicating with the computer before we have graphical interface. It is a mechnical typewriter connected to the computer and the computer reponds to you in a piece of paper.

These days it is not used anymore, But a new one is still being used by linux which is a virtual teletypewriter which you can open using `ctrl + alt + f3` and take note not every machine has the same way to close it but for me `ctrl + alt + f7` works. 

Virtual TTYS or Teletypewriter concept is still used by linux which is what we call terminal now. It is not entirely the same but the concept is the same. Anything that the user start to process will show up if you use `ps a` but only using `ps x` will you see hidden background processes that you the user didn't and those are not connected to any TTYS.

## Common Command Output Breakdown
| USER   | PID  | %CPU | %MEM | VSZ    | RSS   | TTY   | STAT | START | TIME | COMMAND    |
|:-------|:-----|:-----|:-----|:-------|:------|:------|:-----|:------|:-----|:-----------|
| root   | 1    | 0.0  | 0.1  | 168244 | 11728 | ?     | Ss   | Oct02 | 0:04 | /sbin/init |
| ubuntu | 2345 | 0.5  | 0.2  | 24532  | 4120  | pts/0 | R+   | 12:00 | 0:00 | ps aux     |

- **USER** - the user running the process
- **PID or Process ID** - the ID of the process running
- **%CPU** - this is how much *CPU* this process is consuming in percentage
- **%MEM** - this is how much *RAM* this process is consuming in percentage
- **VSZ or Virtual Size** - this is how much virtual memory allocated for this process and its measured in (KiB or Kibibyte)
- **RSS or Resident Set Size** - this is how much *RAM* this process is actually consuming in KiB
- **TTY** - this shows what TTY is running the process. If its `?` then it is a background process
- **STAT** - this is the state of the process
    - `R` - Running or Ready to Run
    - `S` - Sleeping and waiting for something to do
    - `Z` - Zombie, this is a dead process but still hasn't been cleaned up
    - `+` - Foreground process (running in front of you)
- **START** - this is the time or date when it started running
- **TIME** - this is how much CPU is consumed based on time
- **COMMAND** - this is the command that started the process

## Commands
`ps a` - this shows all processes   
`ps u` - this shows all processes but also specify whose user is it  
`ps x` - this forces the machine to show all processes even those that are not started by users  
`ps aux` - this combines all 3 of them to show you everything that is being processesd and you can also see which users is which  
`ps -A` or `ps -e` - this both command do the same thing, this is more minimalist way to show all processes  
`ps -e | grep 'mysqld'` - this shows all processes with 'mysqld' in it  
`ps -e | grep -E  'firefox|chrome'` - this shows all the processes with 'firefox' or 'chrome' in it  
`ps -U root -u root -N` - this shows all processes except those running as root  

---

`top` - this shows all processes in a real-time view


## Source
https://www.cyberciti.biz/faq/show-all-running-processes-in-linux/