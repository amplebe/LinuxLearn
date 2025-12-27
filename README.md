# LinuxLearn
## Day 1
> ### ls Command
- First linux command is ``` ls ```. This is the list command. It allows us to **list the content** of the directory.
- ``` ls --color=no ```
- So, this leads us to the first output, the **colorized list of content.** In order to have it, we need to run
``` ls --color=yes ```
- or, alternatively for now
``` ls --color=auto ```
to clear the screen  `clear`

> #### Get more details with ls Command
- What we pass after the command `-` these are **arguments**. Not switches, parameters, etc.
- `ls -l` - to get More details in list command
- `l` means long listing format.
- `-` indicates that we will pass arguments. We have two ways here
	1. `-` one dash informs the system that we will pass one letter argument, like 'l'
	2. `--` two dashes means that argument will contain more than one letter. Most commonly it will be an english word.
- permissions
- number of hard links. By default every object has 1 hard link
- Owner
- Group, This means that our 'groupmates' have specific access to the file.
- Size. File size in bytes.
- date and time of last modification of the object.
- file name.
- Owner and group. The system keeps and translates them from numerical representation. These are UID for user identifier and GID for group identifier. We can list this information in numeric way, by entering the ls -n command. This works like ls -l, but it changes the user-friendly names to UIDs and GIDs.
Right now we listed all files in alphabetical order.

- List all files - there are many files and directories which are hidden. This generally means that these object are not listed by using standard listing commands (or by standard view in GUI). In Linux these files and directories are present too. There are a lot already in your directory. Linux uses `.` on the beginning of the object's name. We call these files the dotfiles. Ok, let's print the files again. ls - Hm, there are no 'hidden' files. Yes, we have to find a proper argument. this time it will be -a.
- ls -a This command listed much more files than before. A lot of dotfiles! No matter what are they, at least, not now. But two of them needs to be explained. `.` `..`
- The first, . simply means the current directory of the user.
- The second, .. means parent directory.
- `ls .` - will show exactly the same output like simple ls. And `ls ..` shows the parent directory structure!
- Final argument for this section is -A (capital a). While a means all, A means almost all. In this case the command will show all files, except the . and ...
- We can combine multiple arguments in the command. Try run `ls -al` . What can you see?

> Sorting
- ls command has some options built-in. First type of sort we already observed. By default ls sorts the files alphabetically.
- Linux has differente timestamps, three, to be exact.

atime - the last time when file was accessed
mtime - last modification time. By modification we mean change in the file content.
ctime - last metadata modification time. We mean here - permissions change, location of the file, etc.

What is timestamp?

This is the numerical representation of the time. It is the number of seconds passed from Unix epoch which is midnight of 1st of January, 1970.

Well, on the occasion we learned a new command - date. Enough to say, this command shows the current date and time:

date .

The first sort option will be -t. This argument sorts files with the last modification time, newest files come first.

Let's try.

ls -lt

We use two arguments, to observe things better. We can specify exactly the modification time by adding u to the argument list. But please remember, in order to print this information properly you have to use t with another argument (u in this case).

ls -ltu

Ok, now let's print the list and order it by ctime - metadata change.

ls -ltc

Well, not much changed, right? Please execute these commands and carefully observe the output

touch theNewestFile (this creates a new file)
ls -ltu
ls -ltc
echo "hello world!" > file-02 (this will add something to the file)
ls -ltu
ls -ltc
chmod 444 file-01 (this will change the permissions of the file)
ls -ltu
ls -ltc

Please spend some time to understand what and how was printed. We used some commands which are new, but do not waste your time on them now.


Sort content by size
OK, we know how to sort files by time, let's learn how to do it by size.

As usual, we have multiple options to do so.

First, we run this command

ls -s

This shows the short list of files and allocated space. As we already know, we can combine this argument - s - with others. Let's do it.

ls -ls

But this is what you have by default, using ls -l, right? No? You are correct, the answer is no. Take a look on the beginning of each line, this is where you can find, what was added by -s.

Why we used s? I wanted you to pay attention here. When capital S is used, this means sort.

ls -lS it sorts files by size, largest are going first.

So, arguments are case-sensitive, like... everything in Linux :)

Before we use the next command, there is one argument more to be learned. This argument is --human-readable, or better - -h

Let's try.

ls -lh we have printed the size of the files not in bytes, but in more readable form, with K, M, or G, that sort of things.

h use the powers of 1024. So, 1K is a 1 powered by 1024. We have another otion

ls -l --si

which uses powers of 1000. But.. I think no one uses that :)

Ok, let's try to sort with h parameter

ls -lSh

6. Formatting
Different formats
Ok, we are able to sort the list. Now it is time to format it a little.

The first option will be applied to simple ls.

Let's recall, how the simple ls looks like. Now, let's use it with our new argument.

ls -1

Now, please think, why it is obvious thet we do not need to use -1 with -l argument?

--format can be usable when scripting and ls is used for input for other parts of the script.

ls --format=commas will print the files separated by commas. We can use shorter syntax and write

ls -m

Surprise! -l is also the --format option. If you wish to use it in full, use ls --format=long
ls -lQ prints the filenames in quotes

--time-style changes the way how the date is formated in long format. Let's experiment:

ls -l
ls -l --time-style=locale
ls -l --time-style=iso
ls -l --time-style=full-iso


7. Other options and help
A few arguments more
To finalize some usefull arguments, please take a look on these:

ls -al --author prints the username of the creator of the file.

ls -ald prints directories only. Very useful in some circumstances.

ls -ali prints inodes (there will be a lesson about inodes).

ls -alR recursively prints all subdirectories.

ls -alr prints list in the reversed order. So,

ls -alSr is printing... what? :)

Finale
Two last commands in this scenario.

ls --version prints the version of the binary.

All commands which we used here are available in help. How to get the help?

ls --help
