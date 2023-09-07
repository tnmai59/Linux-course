# Information commands
* Ex1:

1.1 Display the name of the current user
```
theia@theia-lemai0509200:/home/project$ whoami
theia
```
1.2  Get basic information about the operating system
```
theia@theia-lemai0509200:/home/project$ uname
Linux

theia@theia-lemai0509200:/home/project$ uname -a
Linux theia-lemai0509200 5.4.0-156-generic #173-Ubuntu SMP Tue Jul 11 07:25:22 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```
1.3 Obtain the user and group identity information
```
theia@theia-lemai0509200:/home/project$ id
uid=1000(theia) gid=1000(theia) groups=1000(theia),27(sudo),100(users)
```
1.4  Get available disk space
```
theia@theia-lemai0509200:/home/project$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
overlay        101986876 57793344  39773296  60% /
tmpfs              65536        0     65536   0% /dev
tmpfs           16361252        0  16361252   0% /sys/fs/cgroup
/dev/vda2      101986876 57793344  39773296  60% /etc/hosts
shm                65536        0     65536   0% /dev/shm
tmpfs           28937800       16  28937784   1% /run/secrets/kubernetes.io/serviceaccount
tmpfs           16361252        0  16361252   0% /proc/acpi
tmpfs           16361252        0  16361252   0% /proc/scsi
tmpfs           16361252        0  16361252   0% /sys/firmware
```

1.5 View currently running processes
```
theia@theia-lemai0509200:/home/project$ ps
   PID TTY          TIME CMD
    92 pts/0    00:00:00 bash
   616 pts/0    00:00:00 ps
```
1.6 Get information on the running processes and system resources
```
theia@theia-lemai0509200:/home/project$ top
Filesystem     1K-blocks     Used Available Use% Mounted on
overlay        101986876 57793344  39773296  60% /
tmpfs              65536        0     65536   0% /dev
tmpfs           16361252        0  16361252   0% /sys/fs/cgroup
/dev/vda2      101986876 57793344  39773296  60% /etc/hosts
shm                65536        0     65536   0% /dev/shm
tmpfs           28937800       16  28937784   1% /run/secrets/kubernetes.io/serviceaccount
tmpfs           16361252        0  16361252   0% /proc/acpi
tmpfs           16361252        0  16361252   0% /proc/scsi
tmpfs           16361252        0  16361252   0%
top - 09:25:09 up 6 days, 23:53,  0 users,  load average: 1.32, 1.01, 0.80
Tasks:  13 total,   1 running,  12 sleeping,   0 stopped,   0 zombie
%Cpu(s):  9.7 us,  3.9 sy,  0.0 ni, 78.9 id,  6.8 wa,  0.0 hi,  0.2 si,  0.4 st
top - 09:25:31 up 6 days, 23:53,  0 users,  load average: 1.68, 1.12, 0.84
Tasks:  13 total,   1 running,  12 sleeping,   0 stopped,   0 zombie
%Cpu(s): 13.0 us,  6.6 sy,  0.0 ni, 76.9 id,  2.4 wa,  0.0 hi,  0.6 si,  0.5 st
KiB Mem : 32722504 total,  2477448 free,  4587328 used, 25657728 buff/cache
KiB Swap:        0 total,        0 free,        0 used. 27650520 avail Mem 

   PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
    59 theia     20   0 1024500  89432  37692 S   0.7  0.3   0:04.00 node        
    70 theia     20   0 1075132  61632  32688 S   0.7  0.2   0:03.62 node        
     1 theia     20   0    4632    776    708 S   0.0  0.0   0:00.01 sh          
     7 theia     20   0   12888   3316   3024 S   0.0  0.0   0:00.01 entrypoint+ 
    35 root      20   0   31320   2900   2620 S   0.0  0.0   0:00.00 cron        
```
1.7 Display message
```
theia@theia-lemai0509200:/home/project$ echo "Welcome to the linux lab"
Welcome to the linux lab
theia@theia-lemai0509200:/home/project$ echo -e "This will be printed \nin two lines"
This will be printed 
in two lines
```
1.8 Display date and time
```
theia@theia-lemai0509200:/home/project$ date
Wed Sep  6 09:28:34 EDT 2023
theia@theia-lemai0509200:/home/project$ date "+%D"
09/06/23
theia@theia-lemai0509200:/home/project$ date "+%d"
06
theia@theia-lemai0509200:/home/project$ date "+%h"
Sep
theia@theia-lemai0509200:/home/project$ date "+%m"
09
theia@theia-lemai0509200:/home/project$ date "+%Y"
2023
theia@theia-lemai0509200:/home/project$ date "+%T"
09:30:23
theia@theia-lemai0509200:/home/project$ date "+%H"
09
```
1.9 View the Reference Manual For a Command
```
theia@theia-lemai0509200:/home/project$ man
What manual page do you want?
theia@theia-lemai0509200:/home/project$ man ls
theia@theia-lemai0509200:/home/project$ man -k .
groovy (1)           - Agile dynamic language for the Java Virtual Machine
TRUNCATE (7)         - empty a table or set of tables
[ (1)                - check file types and compare values
ABORT (7)            - abort the current transaction
accessdb (8)         - dumps the content of a man-db database in a human reada...
aclocal (1)          - manual page for aclocal 1.15.1
aclocal-1.15 (1)     - manual page for aclocal 1.15.1
ALTER_AGGREGATE (7)  - change the definition of an aggregate function
ALTER_COLLATION (7)  - change the definition of a collation
ALTER_CONVERSION (7) - change the definition of a conversion
ALTER_DATABASE (7)   - change a database
ALTER_DEFAULT_PRIVILEGES (7) - define default access privileges
ALTER_DOMAIN (7)     - change the definition of a domain
ALTER_EVENT_TRIGGER (7) - change the definition of an event trigger
ALTER_EXTENSION (7)  - change the definition of an extension
ALTER_FOREIGN_DATA_WRAPPER (7) - change the definition of a foreign-data wrapper
ALTER_FOREIGN_TABLE (7) - change the definition of a foreign table
ALTER_FUNCTION (7)   - change the definition of a function
ALTER_GROUP (7)      - change role name or membership
ALTER_INDEX (7)      - change the definition of an index
ALTER_LANGUAGE (7)   - change the definition of a procedural language
ALTER_LARGE_OBJECT (7) - change the definition of a large object
ALTER_MATERIALIZED_VIEW (7) - change the definition of a materialized view
ALTER_OPERATOR (7)   - change the definition of an operator
ALTER_OPERATOR_CLASS (7) - change the definition of an operator class
ALTER_OPERATOR_FAMILY (7) - change the definition of an operator family
ALTER_POLICY (7)     - change the definition of a row-level security policy
ALTER_PROCEDURE (7)  - change the definition of a procedure
ALTER_PUBLICATION (7) - change the definition of a publication
ALTER_ROLE (7)       - change a database role
ALTER_ROUTINE (7)    - change the definition of a routine
ALTER_RULE (7)       - change the definition of a rule
ALTER_SCHEMA (7)     - change the definition of a schema
ALTER_SEQUENCE (7)   - change the definition of a sequence generator
ALTER_SERVER (7)     - change the definition of a foreign server
ALTER_STATISTICS (7) - change the definition of an extended statistics object
ALTER_SUBSCRIPTION (7) - change the definition of a subscription
ALTER_SYSTEM (7)     - change a server configuration parameter
ALTER_TABLE (7)      - change the definition of a table
ALTER_TABLESPACE (7) - change the definition of a tablespace
ALTER_TEXT_SEARCH_CONFIGURATION (7) - change the definition of a text search c...
ALTER_TEXT_SEARCH_DICTIONARY (7) - change the definition of a text search dict...
ALTER_TEXT_SEARCH_PARSER (7) - change the definition of a text search parser
ALTER_TEXT_SEARCH_TEMPLATE (7) - change the definition of a text search template
ALTER_TRIGGER (7)    - change the definition of a trigger
ALTER_TYPE (7)       - change the definition of a type
ALTER_USER (7)       - change a database role
ALTER_USER_MAPPING (7) - change the definition of a user mapping
ALTER_VIEW (7)       - change the definition of a view
ANALYZE (7)          - collect statistics about a database
apropos (1)          - search the manual page names and descriptions
apt-listchanges (1)  - Show new changelog entries from Debian package archives
arch (1)             - print machine hardware name (same as uname -m)
autoconf (1)         - Generate configuration scripts
autoheader (1)       - Create a template header for configure
autom4te (1)         - Generate files and scripts thanks to M4
automake (1)         - manual page for automake 1.15.1
automake-1.15 (1)    - manual page for automake 1.15.1
autoreconf (1)       - Update generated configuration files
autoscan (1)         - Generate a preliminary configure.in
autoupdate (1)       - Update a configure.in to a newer Autoconf
b2sum (1)            - compute and check BLAKE2 message digest
base32 (1)           - base32 encode/decode data and print to standard output
base64 (1)           - base64 encode/decode data and print to standard output
basename (1)         - strip directory and suffix from filenames
BEGIN (7)            - start a transaction block
calc_tickadj (1)     - Calculates "optimal" value for tick given ntp drift file.
CALL (7)             - invoke a procedure
cat (1)              - concatenate files and print on the standard output
catman (8)           - create or update the pre-formatted manual pages
chcon (1)            - change file security context
CHECKPOINT (7)       - force a write-ahead log checkpoint
chgrp (1)            - change group ownership
chmod (1)            - change file mode bits
chown (1)            - change file owner and group
chroot (8)           - run command or interactive shell with special root dire...
cifsiostat (1)       - Report CIFS statistics.
cksum (1)            - checksum and count the bytes in a file
CLOSE (7)            - close a cursor
CLUSTER (7)          - cluster a table according to an index
clusterdb (1)        - cluster a PostgreSQL database
comm (1)             - compare two sorted files line by line
COMMENT (7)          - define or change the comment of an object
COMMIT (7)           - commit the current transaction
COMMIT_PREPARED (7)  - commit a transaction that was earlier prepared for two-...
common::sense (3pm)  - save a tree AND a kitten, use common::sense!
config.guess (1)     - guess the build system triplet
config.sub (1)       - validate and canonicalize a configuration triplet
COPY (7)             - copy data between a file and a table
cp (1)               - copy files and directories
CREATE_ACCESS_METHOD (7) - define a new access method
CREATE_AGGREGATE (7) - define a new aggregate function
CREATE_CAST (7)      - define a new cast
CREATE_COLLATION (7) - define a new collation
CREATE_CONVERSION (7) - define a new encoding conversion
CREATE_DATABASE (7)  - create a new database
CREATE_DOMAIN (7)    - define a new domain
CREATE_EVENT_TRIGGER (7) - define a new event trigger
CREATE_EXTENSION (7) - install an extension
CREATE_FOREIGN_DATA_WRAPPER (7) - define a new foreign-data wrapper
CREATE_FOREIGN_TABLE (7) - define a new foreign table
CREATE_FUNCTION (7)  - define a new function
CREATE_GROUP (7)     - define a new database role
CREATE_INDEX (7)     - define a new index
CREATE_LANGUAGE (7)  - define a new procedural language
CREATE_MATERIALIZED_VIEW (7) - define a new materialized view
CREATE_OPERATOR (7)  - define a new operator
CREATE_OPERATOR_CLASS (7) - define a new operator class
CREATE_OPERATOR_FAMILY (7) - define a new operator family
CREATE_POLICY (7)    - define a new row-level security policy for a table
CREATE_PROCEDURE (7) - define a new procedure
CREATE_PUBLICATION (7) - define a new publication
CREATE_ROLE (7)      - define a new database role
CREATE_RULE (7)      - define a new rewrite rule
CREATE_SCHEMA (7)    - define a new schema
CREATE_SEQUENCE (7)  - define a new sequence generator
CREATE_SERVER (7)    - define a new foreign server
CREATE_STATISTICS (7) - define extended statistics
CREATE_SUBSCRIPTION (7) - define a new subscription
CREATE_TABLE (7)     - define a new table
CREATE_TABLE_AS (7)  - define a new table from the results of a query
CREATE_TABLESPACE (7) - define a new tablespace
CREATE_TEXT_SEARCH_CONFIGURATION (7) - define a new text search configuration
CREATE_TEXT_SEARCH_DICTIONARY (7) - define a new text search dictionary
CREATE_TEXT_SEARCH_PARSER (7) - define a new text search parser
CREATE_TEXT_SEARCH_TEMPLATE (7) - define a new text search template
CREATE_TRANSFORM (7) - define a new transform
CREATE_TRIGGER (7)   - define a new trigger
CREATE_TYPE (7)      - define a new data type
CREATE_USER (7)      - define a new database role
CREATE_USER_MAPPING (7) - define a new mapping of a user to a foreign server
CREATE_VIEW (7)      - define a new view
createdb (1)         - create a new PostgreSQL database
createuser (1)       - define a new PostgreSQL user account
csplit (1)           - split a file into sections determined by context lines
cut (1)              - remove sections from each line of files
date (1)             - print or set the system date and time
dd (1)               - convert and copy a file
DEALLOCATE (7)       - deallocate a prepared statement
DECLARE (7)          - define a cursor
DELETE (7)           - delete rows of a table
df (1)               - report file system disk space usage
dh_autotools-dev_restoreconfig (1) - restore config.sub and config.guess
dh_autotools-dev_updateconfig (1) - update config.sub and config.guess
dir (1)              - list directory contents
dircolors (1)        - color setup for ls
dirname (1)          - strip last component from file name
DISCARD (7)          - discard session state
DO (7)               - execute an anonymous code block
DROP_ACCESS_METHOD (7) - remove an access method
DROP_AGGREGATE (7)   - remove an aggregate function
DROP_CAST (7)        - remove a cast
DROP_COLLATION (7)   - remove a collation
DROP_CONVERSION (7)  - remove a conversion
DROP_DATABASE (7)    - remove a database
DROP_DOMAIN (7)      - remove a domain
DROP_EVENT_TRIGGER (7) - remove an event trigger
DROP_EXTENSION (7)   - remove an extension
DROP_FOREIGN_DATA_WRAPPER (7) - remove a foreign-data wrapper
DROP_FOREIGN_TABLE (7) - remove a foreign table
DROP_FUNCTION (7)    - remove a function
DROP_GROUP (7)       - remove a database role
DROP_INDEX (7)       - remove an index
DROP_LANGUAGE (7)    - remove a procedural language
DROP_MATERIALIZED_VIEW (7) - remove a materialized view
DROP_OPERATOR (7)    - remove an operator
DROP_OPERATOR_CLASS (7) - remove an operator class
DROP_OPERATOR_FAMILY (7) - remove an operator family
DROP_OWNED (7)       - remove database objects owned by a database role
DROP_POLICY (7)      - remove a row-level security policy from a table
DROP_PROCEDURE (7)   - remove a procedure
DROP_PUBLICATION (7) - remove a publication
DROP_ROLE (7)        - remove a database role
DROP_ROUTINE (7)     - remove a routine
DROP_RULE (7)        - remove a rewrite rule
DROP_SCHEMA (7)      - remove a schema
DROP_SEQUENCE (7)    - remove a sequence
DROP_SERVER (7)      - remove a foreign server descriptor
DROP_STATISTICS (7)  - remove extended statistics
DROP_SUBSCRIPTION (7) - remove a subscription
DROP_TABLE (7)       - remove a table
DROP_TABLESPACE (7)  - remove a tablespace
DROP_TEXT_SEARCH_CONFIGURATION (7) - remove a text search configuration
DROP_TEXT_SEARCH_DICTIONARY (7) - remove a text search dictionary
DROP_TEXT_SEARCH_PARSER (7) - remove a text search parser
DROP_TEXT_SEARCH_TEMPLATE (7) - remove a text search template
DROP_TRANSFORM (7)   - remove a transform
DROP_TRIGGER (7)     - remove a trigger
DROP_TYPE (7)        - remove a data type
DROP_USER (7)        - remove a database role
DROP_USER_MAPPING (7) - remove a user mapping for a foreign server
DROP_VIEW (7)        - remove a view
dropdb (1)           - remove a PostgreSQL database
dropuser (1)         - remove a PostgreSQL user account
du (1)               - estimate file space usage
echo (1)             - display a line of text
END (7)              - commit the current transaction
env (1)              - run a program in a modified environment
EXECUTE (7)          - execute a prepared statement
expand (1)           - convert tabs to spaces
EXPLAIN (7)          - show the execution plan of a statement
expr (1)             - evaluate expressions
factor (1)           - factor numbers
false (1)            - do nothing, unsuccessfully
FETCH (7)            - retrieve rows from a query using a cursor
fmt (1)              - simple optimal text formatter
fold (1)             - wrap each input line to fit in specified width
gh (1)               - GitHub CLI
gh-alias (1)         - Create command shortcuts
gh-alias-delete (1)  - Delete an alias
gh-alias-list (1)    - List your aliases
gh-alias-set (1)     - Create a shortcut for a gh command
gh-api (1)           - Make an authenticated GitHub API request
gh-auth (1)          - Authenticate gh and git with GitHub
gh-auth-login (1)    - Authenticate with a GitHub host
gh-auth-logout (1)   - Log out of a GitHub host
gh-auth-refresh (1)  - Refresh stored authentication credentials
gh-auth-setup-git (1) - Configure git to use GitHub CLI as a credential helper
gh-auth-status (1)   - View authentication status
gh-browse (1)        - Open the repository in the browser
gh-codespace (1)     - Connect to and manage codespaces
gh-codespace-code (1) - Open a codespace in Visual Studio Code
gh-codespace-cp (1)  - Copy files between local and remote file systems
gh-codespace-create (1) - Create a codespace
gh-codespace-delete (1) - Delete codespaces
gh-codespace-edit (1) - Edit a codespace
gh-codespace-jupyter (1) - Open a codespace in JupyterLab
gh-codespace-list (1) - List codespaces
gh-codespace-logs (1) - Access codespace logs
gh-codespace-ports (1) - List ports in a codespace
gh-codespace-ports-forward (1) - Forward ports
gh-codespace-ports-visibility (1) - Change the visibility of the forwarded port
gh-codespace-ssh (1) - SSH into a codespace
gh-codespace-stop (1) - Stop a running codespace
gh-completion (1)    - Generate shell completion scripts
gh-config (1)        - Manage configuration for gh
gh-config-get (1)    - Print the value of a given configuration key
gh-config-list (1)   - Print a list of configuration keys and values
gh-config-set (1)    - Update configuration with a value for the given key
gh-extension (1)     - Manage gh extensions
gh-extension-create (1) - Create a new extension
gh-extension-exec (1) - Execute an installed extension
gh-extension-install (1) - Install a gh extension from a repository
gh-extension-list (1) - List installed extension commands
gh-extension-remove (1) - Remove an installed extension
gh-extension-upgrade (1) - Upgrade installed extensions
gh-gist (1)          - Manage gists
gh-gist-clone (1)    - Clone a gist locally
gh-gist-create (1)   - Create a new gist
gh-gist-delete (1)   - Delete a gist
gh-gist-edit (1)     - Edit one of your gists
gh-gist-list (1)     - List your gists
gh-gist-view (1)     - View a gist
gh-gpg-key (1)       - Manage GPG keys
gh-gpg-key-add (1)   - Add a GPG key to your GitHub account
gh-gpg-key-list (1)  - Lists GPG keys in your GitHub account
gh-issue (1)         - Manage issues
gh-issue-close (1)   - Close issue
gh-issue-comment (1) - Add a comment to an issue
gh-issue-create (1)  - Create a new issue
gh-issue-delete (1)  - Delete issue
gh-issue-edit (1)    - Edit an issue
gh-issue-list (1)    - List issues in a repository
gh-issue-reopen (1)  - Reopen issue
gh-issue-status (1)  - Show status of relevant issues
gh-issue-transfer (1) - Transfer issue to another repository
gh-issue-view (1)    - View an issue
gh-label (1)         - Manage labels
gh-label-clone (1)   - Clones labels from one repository to another
gh-label-create (1)  - Create a new label
gh-label-delete (1)  - Delete a label from a repository
gh-label-edit (1)    - Edit a label
gh-label-list (1)    - List labels in a repository
gh-pr (1)            - Manage pull requests
gh-pr-checkout (1)   - Check out a pull request in git
gh-pr-checks (1)     - Show CI status for a single pull request
gh-pr-close (1)      - Close a pull request
gh-pr-comment (1)    - Add a comment to a pull request
gh-pr-create (1)     - Create a pull request
gh-pr-diff (1)       - View changes in a pull request
gh-pr-edit (1)       - Edit a pull request
gh-pr-list (1)       - List pull requests in a repository
gh-pr-merge (1)      - Merge a pull request
gh-pr-ready (1)      - Mark a pull request as ready for review
gh-pr-reopen (1)     - Reopen a pull request
gh-pr-review (1)     - Add a review to a pull request
gh-pr-status (1)     - Show status of relevant pull requests
gh-pr-view (1)       - View a pull request
gh-release (1)       - Manage releases
gh-release-create (1) - Create a new release
gh-release-delete (1) - Delete a release
gh-release-delete-asset (1) - Delete an asset from a release
gh-release-download (1) - Download release assets
gh-release-edit (1)  - Edit a release
gh-release-list (1)  - List releases in a repository
gh-release-upload (1) - Upload assets to a release
gh-release-view (1)  - View information about a release
gh-repo (1)          - Manage repositories
gh-repo-archive (1)  - Archive a repository
gh-repo-clone (1)    - Clone a repository locally
gh-repo-create (1)   - Create a new repository
gh-repo-delete (1)   - Delete a repository
gh-repo-deploy-key (1) - Manage deploy keys in a repository
gh-repo-deploy-key-add (1) - Add a deploy key to a GitHub repository
gh-repo-deploy-key-delete (1) - Delete a deploy key from a GitHub repository
gh-repo-deploy-key-list (1) - List deploy keys in a GitHub repository
gh-repo-edit (1)     - Edit repository settings
gh-repo-fork (1)     - Create a fork of a repository
gh-repo-list (1)     - List repositories owned by user or organization
gh-repo-rename (1)   - Rename a repository
gh-repo-sync (1)     - Sync a repository
gh-repo-view (1)     - View a repository
gh-run (1)           - View details about workflow runs
gh-run-cancel (1)    - Cancel a workflow run
gh-run-download (1)  - Download artifacts generated by a workflow run
gh-run-list (1)      - List recent workflow runs
gh-run-rerun (1)     - Rerun a failed run
gh-run-view (1)      - View a summary of a workflow run
gh-run-watch (1)     - Watch a run until it completes, showing its progress
gh-search (1)        - Search for repositories, issues, and pull requests
gh-search-issues (1) - Search for issues
gh-search-prs (1)    - Search for pull requests
gh-search-repos (1)  - Search for repositories
gh-secret (1)        - Manage GitHub secrets
gh-secret-delete (1) - Delete secrets
gh-secret-list (1)   - List secrets
gh-secret-set (1)    - Create or update secrets
gh-ssh-key (1)       - Manage SSH keys
gh-ssh-key-add (1)   - Add an SSH key to your GitHub account
gh-ssh-key-list (1)  - Lists SSH keys in your GitHub account
gh-status (1)        - Print information about relevant issues, pull requests,...
gh-workflow (1)      - View details about GitHub Actions workflows
gh-workflow-disable (1) - Disable a workflow
gh-workflow-enable (1) - Enable a workflow
gh-workflow-list (1) - List workflows
gh-workflow-run (1)  - Run a workflow by creating a workflow_dispatch event
gh-workflow-view (1) - View the summary of a workflow
GRANT (7)            - define access privileges
grape (1)            - inspection and management of the local grape cache used...
groovyc (1)          - compiler for groovy source files
groups (1)           - print the groups a user is in
head (1)             - output the first part of files
hostid (1)           - print the numeric identifier for the current host
id (1)               - print real and effective user and group IDs
ifnames (1)          - Extract CPP conditionals from a set of files
IMPORT_FOREIGN_SCHEMA (7) - import table definitions from a foreign server
initdb (1)           - create a new PostgreSQL database cluster
INSERT (7)           - create new rows in a table
install (1)          - copy files and set attributes
iostat (1)           - Report Central Processing Unit (CPU) statistics and inp...
java (1)             - Launches a Java application.
jjs (1)              - Invokes the Nashorn engine.
join (1)             - join lines of two files on a common field
JSON (3pm)           - JSON (JavaScript Object Notation) encoder/decoder
JSON::backportPP (3pm) - JSON::XS compatible pure-Perl module.
JSON::backportPP::Boolean (3pm) - dummy module providing JSON::PP::Boolean
JSON::backportPP::Compat5005 (3pm) - Helper module in using JSON::PP in Perl 5...
JSON::backportPP::Compat5006 (3pm) - Helper module in using JSON::PP in Perl 5.6
JSON::XS (3pm)       - JSON serialising/deserialising, done correctly and fast
JSON::XS::Boolean (3pm) - dummy module providing JSON::XS::Boolean
json_xs (1p)         - JSON::XS commandline utility
keytool (1)          - Manages a keystore (database) of cryptographic keys, X....
lexgrog (1)          - parse header information in man pages
link (1)             - call the link function to create a link to a file
LISTEN (7)           - listen for a notification
ln (1)               - make links between files
LOAD (7)             - load a shared library file
LOCK (7)             - lock a table
logname (1)          - print user's login name
logrotate (5)        - rotates, compresses, and mails system logs
logrotate (8)        - rotates, compresses, and mails system logs
logrotate.conf (5)   - rotates, compresses, and mails system logs
ls (1)               - list directory contents
m4 (1)               - macro processor
man (1)              - an interface to the on-line reference manuals
manconv (1)          - convert manual page from one encoding to another
mandb (8)            - create or update the manual page index caches
manpath (1)          - determine search path for manual pages
manpath (5)          - format of the /etc/manpath.config file
md5sum (1)           - compute and check MD5 message digest
md5sum.textutils (1) - compute and check MD5 message digest
MERGE (7)            - conditionally insert, update, or delete rows of a table
mkdir (1)            - make directories
mkfifo (1)           - make FIFOs (named pipes)
mknod (1)            - make block or character special files
mktemp (1)           - create a temporary file or directory
MOVE (7)             - position a cursor
mpstat (1)           - Report processors related statistics.
mv (1)               - move (rename) files
ncurses5-config (1)  - helper script for ncurses libraries
nice (1)             - run a program with modified scheduling priority
nl (1)               - number lines of files
nohup (1)            - run a command immune to hangups, with output to a non-tty
NOTIFY (7)           - generate a notification
nproc (1)            - print the number of processing units available
ntp-keygen (8)       - Create a NTP host key
ntp-wait (8)         - Wait for ntpd to stabilize the system clock
ntp.conf (5)         - Network Time Protocol (NTP) daemon configuration file f...
ntp.keys (5)         - NTP symmetric key file format
ntpd (8)             - NTP daemon program
ntpdc (1)            - vendor-specific NTPD control program
ntpq (1)             - standard NTP query program
ntpsweep (1)         - Sweep NTP Servers and Report Relationships
ntptime (8)          - read kernel time variables
ntptrace (1)         - Trace peers of an NTP server
numfmt (1)           - Convert numbers from/to human-readable strings
od (1)               - dump files in octal and other formats
oid2name (1)         - resolve OIDs and file nodes in a PostgreSQL data directory
orbd (1)             - Enables clients to locate and call persistent objects o...
pack200 (1)          - Packages a JAR file into a compressed pack200 file for ...
paste (1)            - merge lines of files
pathchk (1)          - check whether file names are valid or portable
pg_amcheck (1)       - checks for corruption in one or more PostgreSQL databases
pg_archivecleanup (1) - clean up PostgreSQL WAL archive files
pg_backupcluster (1) - simple pg_basebackup and pg_dump front-end
pg_basebackup (1)    - take a base backup of a PostgreSQL cluster
pg_buildext (1)      - Build and install a PostgreSQL extension
pg_checksums (1)     - enable, disable or check data checksums in a PostgreSQL...
pg_config (1)        - retrieve information about the installed version of Pos...
pg_conftool (1)      - read and edit PostgreSQL cluster configuration files
pg_controldata (1)   - display control information of a PostgreSQL database cl...
pg_createcluster (1) - create a new PostgreSQL cluster
pg_ctl (1)           - initialize, start, stop, or control a PostgreSQL server
pg_ctlcluster (1)    - start/stop/restart/reload a PostgreSQL cluster
pg_dropcluster (1)   - completely delete a PostgreSQL cluster
pg_dump (1)          - extract a PostgreSQL database into a script file or oth...
pg_dumpall (1)       - extract a PostgreSQL database cluster into a script file
pg_getwal (1)        - retrieve a WAL file from a pg_receivewal archive
pg_isready (1)       - check the connection status of a PostgreSQL server
pg_lsclusters (1)    - show information about all PostgreSQL clusters
pg_receivewal (1)    - stream write-ahead logs from a PostgreSQL server
pg_recvlogical (1)   - control PostgreSQL logical decoding streams
pg_renamecluster (1) - rename a PostgreSQL cluster
pg_resetwal (1)      - reset the write-ahead log and other control information...
pg_restore (1)       - restore a PostgreSQL database from an archive file crea...
pg_restorecluster (1) - Restore from a pg_backupcluster backup
pg_rewind (1)        - synchronize a PostgreSQL data directory with another da...
pg_test_fsync (1)    - determine fastest wal_sync_method for PostgreSQL
pg_test_timing (1)   - measure timing overhead
pg_updatedicts (8)   - build PostgreSQL dictionaries from myspell/hunspell ones
pg_upgrade (1)       - upgrade a PostgreSQL server instance
pg_upgradecluster (1) - upgrade an existing PostgreSQL cluster to a new major ...
pg_verifybackup (1)  - verify the integrity of a base backup of a PostgreSQL c...
pg_virtualenv (1)    - Create a throw-away PostgreSQL environment for running ...
pg_waldump (1)       - display a human-readable rendering of the write-ahead l...
pg_wrapper (1)       - wrapper for PostgreSQL client commands
pg_wrapper (7)       - wrapper for PostgreSQL client commands
pgbench (1)          - run a benchmark test on PostgreSQL
pidstat (1)          - Report statistics for Linux tasks.
ping (1)             - send ICMP ECHO_REQUEST packets to network hosts
ping6 (1)            - Packets to network hosts
pinky (1)            - lightweight finger
postgres (1)         - PostgreSQL database server
postgresql-common (7) - wrapper for PostgreSQL client commands
postgresqlrc (5)     - Per-user PostgreSQL cluster configuration
postmaster (1)       - PostgreSQL database server
pr (1)               - convert text files for printing
PREPARE (7)          - prepare a statement for execution
PREPARE_TRANSACTION (7) - prepare the current transaction for two-phase commit
printenv (1)         - print all or part of environment
printf (1)           - format and print data
psql (1)             - PostgreSQL interactive terminal
ptx (1)              - produce a permuted index of file contents
pwd (1)              - print name of current/working directory
readlink (1)         - print resolved symbolic links or canonical file names
realpath (1)         - print the resolved path
REASSIGN_OWNED (7)   - change the ownership of database objects owned by a dat...
REFRESH_MATERIALIZED_VIEW (7) - replace the contents of a materialized view
REINDEX (7)          - rebuild indexes
reindexdb (1)        - reindex a PostgreSQL database
RELEASE_SAVEPOINT (7) - destroy a previously defined savepoint
RESET (7)            - restore the value of a run-time parameter to the defaul...
REVOKE (7)           - remove access privileges
rm (1)               - remove files or directories
rmdir (1)            - remove empty directories
rmid (1)             - Starts the activation system daemon that enables object...
rmiregistry (1)      - Starts a remote object registry on the specified port o...
ROLLBACK (7)         - abort the current transaction
ROLLBACK_PREPARED (7) - cancel a transaction that was earlier prepared for two...
ROLLBACK_TO_SAVEPOINT (7) - roll back to a savepoint
runcon (1)           - run command with specified security context
sa1 (8)              - Collect and store binary data in the system activity da...
sa2 (8)              - Create a report from the current standard system activi...
sadc (8)             - System activity data collector.
sadf (1)             - Display data collected by sar in multiple formats.
sar (1)              - Collect, report, or save system activity information.
sar.sysstat (1)      - Collect, report, or save system activity information.
SAVEPOINT (7)        - define a new savepoint within the current transaction
SECURITY_LABEL (7)   - define or change a security label applied to an object
SELECT (7)           - retrieve rows from a table or view
SELECT_INTO (7)      - define a new table from the results of a query
seq (1)              - print a sequence of numbers
servertool (1)       - Provides an easy-to-use interface for developers to reg...
SET (7)              - change a run-time parameter
SET_CONSTRAINTS (7)  - set constraint check timing for the current transaction
SET_ROLE (7)         - set the current user identifier of the current session
SET_SESSION_AUTHORIZATION (7) - set the session user identifier and the curren...
SET_TRANSACTION (7)  - set the characteristics of the current transaction
sha1sum (1)          - compute and check SHA1 message digest
sha224sum (1)        - compute and check SHA224 message digest
sha256sum (1)        - compute and check SHA256 message digest
sha384sum (1)        - compute and check SHA384 message digest
sha512sum (1)        - compute and check SHA512 message digest
SHOW (7)             - show the value of a run-time parameter
shred (1)            - overwrite a file to hide its contents, and optionally d...
shuf (1)             - generate random permutations
sleep (1)            - delay for a specified amount of time
sntp (1)             - standard Simple Network Time Protocol client program
sort (1)             - sort lines of text files
split (1)            - split a file into pieces
START_TRANSACTION (7) - start a transaction block
stat (1)             - display file or file system status
stdbuf (1)           - Run COMMAND, with modified buffering operations for its...
stty (1)             - change and print terminal line settings
sum (1)              - checksum and count the blocks in a file
sync (1)             - Synchronize cached writes to persistent storage
sysstat (5)          - sysstat configuration file.
TABLE (7)            - retrieve rows from a table or view
tac (1)              - concatenate and print files in reverse
tail (1)             - output the last part of files
tapestat (1)         - Report tape statistics.
tee (1)              - read from standard input and write to standard output a...
test (1)             - check file types and compare values
timeout (1)          - run a command with a time limit
tnameserv (1)        - Interface Definition Language (IDL).
touch (1)            - change file timestamps
tr (1)               - translate or delete characters
true (1)             - do nothing, successfully
truncate (1)         - shrink or extend the size of a file to the specified size
tsort (1)            - perform topological sort
tty (1)              - print the file name of the terminal connected to standa...
Types::Serialiser (3pm) - simple data types for common serialisation formats
Types::Serialiser::Error (3pm) - dummy module for Types::Serialiser
uname (1)            - print system information
unexpand (1)         - convert spaces to tabs
uniq (1)             - report or omit repeated lines
unlink (1)           - call the unlink function to remove the specified file
UNLISTEN (7)         - stop listening for a notification
unpack200 (1)        - Transforms a packed file produced by pack200(1) into a ...
UPDATE (7)           - update rows of a table
update-leap (1)      - leap-seconds file manager/updater
user_clusters (5)    - File linking users to PostgreSQL clusters
users (1)            - print the user names of users currently logged in to th...
VACUUM (7)           - garbage-collect and optionally analyze a database
vacuumdb (1)         - garbage-collect and analyze a PostgreSQL database
vacuumlo (1)         - remove orphaned large objects from a PostgreSQL database
VALUES (7)           - compute a set of rows
vdir (1)             - list directory contents
wc (1)               - print newline, word, and byte counts for each file
whatis (1)           - display one-line manual page descriptions
who (1)              - show who is logged on
whoami (1)           - print effective userid
WITH (7)             - retrieve rows from a table or view
Xsession (5)         - initialize X session
Xsession.options (5) - configuration options for Xsession (5)
yes (1)              - output a string repeatedly until killed
zsoelim (1)          - satisfy .so requests in roff input
ccmake (1)           - CMake Curses Dialog Command-Line Reference
cmake (1)            - CMake Command-Line Reference
cmake-buildsystem (7) - CMake Buildsystem Reference
cmake-commands (7)   - CMake Language Command Reference
cmake-compile-features (7) - CMake Compile Features Reference
cmake-developer (7)  - CMake Developer Reference
cmake-env-variables (7) - CMake Environment Variables Reference
cmake-file-api (7)   - CMake File-Based API
cmake-generator-expressions (7) - CMake Generator Expressions
cmake-generators (7) - CMake Generators Reference
cmake-gui (1)        - CMake GUI Command-Line Reference
cmake-language (7)   - CMake Language Reference
cmake-modules (7)    - CMake Modules Reference
cmake-packages (7)   - CMake Packages Reference
cmake-policies (7)   - CMake Policies Reference
cmake-presets (7)    - CMakePresets.json
cmake-properties (7) - CMake Properties Reference
cmake-qt (7)         - CMake Qt Features Reference
cmake-server (7)     - CMake Server
cmake-toolchains (7) - CMake Toolchains Reference
cmake-variables (7)  - CMake Variables Reference
cpack (1)            - CPack Command-Line Reference
cpack-generators (7) - CPack Generator Reference
ctest (1)            - CTest Command-Line Reference
```
* Practice exercises
1. Get basic information about the operating system.
```
theia@theia-lemai0509200:/home/project$ uname
Linux
```
2. View all running processes on the system.
```
theia@theia-lemai0509200:/home/project$ ps -e
```
3. Get the table of processes and sort by memory usage.
```
theia@theia-lemai0509200:/home/project$ top
```
4. Display the current time.
```
theia@theia-lemai0509200:/home/project$ date "+%T"
09:37:32
```
5.
```
theia@theia-lemai0509200:/home/project$ echo -e "Hello! \nGoodbye!"
Hello! 
Goodbye!
```
# Navigating and Managing Files and Directories
* Ex 1: Navigating Files and Directories

1.1  Get the location of the present working directory
```
theia@theia-lemai0509200:/home/project$ pwd
/home/project
```
1.2 List the files and directories in a directory
```
theia@theia-lemai0509200:/home/project$ ls

theia@theia-lemai0509200:/home/project$ ls /bin
bash
bunzip2
bzcat
bzcmp
bzdiff
bzegrep
bzexe
bzfgrep
bzgrep
bzip2
bzip2recover
bzless
bzmore
cat
chgrp
chmod
chown
cp
dash
date
dd
df
dir
dmesg
dnsdomainname
domainname
echo
egrep
false
fgrep
findmnt
fuser
grep
gunzip
gzexe
gzip
hostname
kill
less
lessecho
lessfile
lesskey
lesspipe
ln
login
ls
lsblk
mkdir
mknod
mktemp
more
mount
mountpoint
mv
nano
netstat
nisdomainname
pidof
ping
ping6
ps
pwd
rbash
readlink
rm
rmdir
rnano
run-parts
sed
sh
sh.distrib
sleep
stty
su
sync
tar
tempfile
touch
true
umount
uname
uncompress
vdir
wdctl
which
ypdomainname
zcat
zcmp
zdiff
zegrep
zfgrep
zforce
zgrep
zless
zmore
znew

theia@theia-lemai0509200:/home/project$ ls /bin/ls
/bin/ls

theia@theia-lemai0509200:/home/project$ ls /bin/b*
/bin/bash
/bin/bunzip2
/bin/bzcat
/bin/bzcmp
/bin/bzdiff
/bin/bzegrep
/bin/bzexe
/bin/bzfgrep
/bin/bzgrep
/bin/bzip2
/bin/bzip2recover
/bin/bzless
/bin/bzmore

theia@theia-lemai0509200:/home/project$ ls /bin/*r
/bin/bzip2recover
/bin/dir
/bin/fuser
/bin/mkdir
/bin/rmdir
/bin/tar
/bin/vdir

theia@theia-lemai0509200:/home/project$ ls -l
total 0


```
* Ex2: Creating Files and Directories

2.1 Create a directory
```
theia@theia-lemai0509200:/home/project$ mkdir scripts
theia@theia-lemai0509200:/home/project$ ls
scripts
```
2.2 Change your current working directory
```
theia@theia-lemai0509200:/home/project$ cd scripts
theia@theia-lemai0509200:/home/project/scripts$ 
theia@theia-lemai0509200:/home/project/scripts$ pwd
/home/project/scripts
theia@theia-lemai0509200:/home/project/scripts$ cd
theia@theia-lemai0509200:~$ pwd
/home/theia
```
2.3 Create an empty file
```
theia@theia-lemai0509200:~$ touch myfile.txt
theia@theia-lemai0509200:~$ ls
docker-compose         myfile.txt    skills-network-extension-v0.1.0.tgz
dsdriver               node_modules  src-gen
entrypoint.sh          package.json  webpack.config.js
gen-webpack.config.js  plugins       yarn.lock
javasharedresources    postgres
lib                    README.md
theia@theia-lemai0509200:~$ touch myfile.txt
theia@theia-lemai0509200:~$ date -r myfile.txt
Wed Sep  6 21:47:28 EDT 2023
```
* Ex3: Managing Files and Directories

3.1 Search for and locate files
```
theia@theia-lemai0509200:~$ find /etc -name \'*.txt\'
find: ‘/etc/ssl/private’: Permission denied
```
3.2 Remove files
```
theia@theia-lemai0509200:~$ ls
docker-compose         myfile.txt    skills-network-extension-v0.1.0.tgz
dsdriver               node_modules  src-gen
entrypoint.sh          package.json  webpack.config.js
gen-webpack.config.js  plugins       yarn.lock
javasharedresources    postgres
lib                    README.md
theia@theia-lemai0509200:~$ rm -i myfile.txt
rm: remove regular empty file 'myfile.txt'? y
theia@theia-lemai0509200:~$ ls
docker-compose         lib           README.md
dsdriver               node_modules  skills-network-extension-v0.1.0.tgz
entrypoint.sh          package.json  src-gen
gen-webpack.config.js  plugins       webpack.config.js
javasharedresources    postgres      yarn.lock
```
3.3 Move and rename
```
theia@theia-lemai0509200:~$ touch users.txt
theia@theia-lemai0509200:~$ ls
docker-compose         node_modules                         src-gen
dsdriver               package.json                         users.txt
entrypoint.sh          plugins                              webpack.config.js
gen-webpack.config.js  postgres                             yarn.lock
javasharedresources    README.md
lib                    skills-network-extension-v0.1.0.tgz
theia@theia-lemai0509200:~$ mv users.txt user-info.txt
theia@theia-lemai0509200:~$ ls
docker-compose         node_modules                         src-gen
dsdriver               package.json                         user-info.txt
entrypoint.sh          plugins                              webpack.config.js
gen-webpack.config.js  postgres                             yarn.lock
javasharedresources    README.md
lib                    skills-network-extension-v0.1.0.tgz

theia@theia-lemai0509200:~$ mv user-info.txt /tmp
theia@theia-lemai0509200:~$ ls -l /tmp
```
3.4 Copy files
```
theia@theia-lemai0509200:~$ cp /tmp/user-info.txt user-info.txt
theia@theia-lemai0509200:~$ ls
docker-compose         node_modules                         src-gen
dsdriver               package.json                         user-info.txt
entrypoint.sh          plugins                              webpack.config.js
gen-webpack.config.js  postgres                             yarn.lock
javasharedresources    README.md
lib                    skills-network-extension-v0.1.0.tgz
```
* Practice exercises

1.  Display the contents of the `/home` directory.
```
theia@theia-lemai0509200:~$ ls
docker-compose         node_modules                         src-gen
dsdriver               package.json                         user-info.txt
entrypoint.sh          plugins                              users.txt
gen-webpack.config.js  postgres                             webpack.config.js
javasharedresources    README.md                            yarn.lock
lib                    skills-network-extension-v0.1.0.tgz
```

2. Ensure that you are in your home directory.
```
theia@theia-lemai0509200:~$ pwd
/home/theia
```
3. Create a new directory called `tmp` and verify its creation.
```
theia@theia-lemai0509200:~$ mkdir tmp
theia@theia-lemai0509200:~$ ls
docker-compose         node_modules                         src-gen
dsdriver               package.json                         tmp
entrypoint.sh          plugins                              user-info.txt
gen-webpack.config.js  postgres                             users.txt
javasharedresources    README.md                            webpack.config.js
lib                    skills-network-extension-v0.1.0.tgz  yarn.lock
```
4. Create a new, empty file named `display.sh` in the `tmp` directory, and verify its creation
```
theia@theia-lemai0509200:~$ cd tmp
theia@theia-lemai0509200:~/tmp$ touch display.sh
theia@theia-lemai0509200:~/tmp$ ls
display.sh
```
5.  Create a copy of` display.sh`, called `report.sh`, within the same directory.
```
theia@theia-lemai0509200:~/tmp$ cp display.sh report.sh
theia@theia-lemai0509200:~/tmp$ ls
display.sh  report.sh
```
6. Move your copied file, `report.sh`, up one level in the directory tree to the parent directory. Verify your changes.
```
theia@theia-lemai0509200:~/tmp$ mv report.sh ../
theia@theia-lemai0509200:~/tmp$ ls
display.sh
theia@theia-lemai0509200:~/tmp$ ls ../
docker-compose         package.json                         tmp
dsdriver               plugins                              user-info.txt
entrypoint.sh          postgres                             users.txt
gen-webpack.config.js  README.md                            webpack.config.js
javasharedresources    report.sh                            yarn.lock
lib                    skills-network-extension-v0.1.0.tgz
node_modules           src-gen
```
7. Delete the file `display.sh`
```
theia@theia-lemai0509200:~/tmp$ rm display.sh
theia@theia-lemai0509200:~/tmp$ ls
```
8. List the files in `/etc` directory in the ascending order of their access time.
```
theia@theia-lemai0509200:~/tmp$ ls -ltr /etc/
total 668
-rw-r--r-- 1 root     root        34 Jan 27  2016 ld.so.conf
-rw-r--r-- 1 root     root       367 Jan 27  2016 bindresvport.blacklist
-rw-r--r-- 1 root     root     24301 Jul 15  2016 mime.types
-rw-r--r-- 1 root     root       449 Jul 15  2016 mailcap.order
-rw-r--r-- 1 root     root       497 Oct  5  2016 nsswitch.conf
-rw-r--r-- 1 root     root     19183 Dec 25  2016 services
-rw-r--r-- 1 root     root       887 Dec 25  2016 rpc
-rw-r--r-- 1 root     root      2932 Dec 25  2016 protocols
drwxr-xr-x 2 root     root      4096 Dec 25  2016 network
...

```
9.  Copy the file `/var/log/bootstrap.log` to your current directory.
```
theia@theia-lemai0509200:~/tmp$ cp /var/log/bootstrap.log .
theia@theia-lemai0509200:~/tmp$ ls
bootstrap.log
```
# Access Control Commands
* Ex1: Viewing and modifying file access permissions

1.1 Viewing and modifying file access permissions
```
theia@theia-lemai0509200:~/tmp$ cd /home/project
theia@theia-lemai0509200:/home/project$ wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-LX0117EN-SkillsNetwork/labs/module%201/usdoi.txt
--2023-09-06 22:14:09--  https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-LX0117EN-SkillsNetwork/labs/module%201/usdoi.txt
Resolving cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud (cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud)... 169.63.118.104
Connecting to cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud (cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud)|169.63.118.104|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8121 (7.9K) [text/plain]
Saving to: ‘usdoi.txt’

usdoi.txt            100%[===================>]   7.93K  --.-KB/s    in 0s      

2023-09-06 22:14:09 (869 MB/s) - ‘usdoi.txt’ saved [8121/8121]

theia@theia-lemai0509200:/home/project$ ls -l usdoi.txt
-rw-r--r-- 1 theia users 8121 Sep 28  2022 usdoi.txt
```
1.2 Change file access permissions
```
theia@theia-lemai0509200:/home/project$ chmod -r usdoi.txt               
theia@theia-lemai0509200:/home/project$ ls -l usdoi.txt
--w------- 1 theia users 8121 Sep 28  2022 usdoi.txt
theia@theia-lemai0509200:/home/project$ chmod +r usdoi.txt                
theia@theia-lemai0509200:/home/project$ ls -l usdoi.txt
-rw-r--r-- 1 theia users 8121 Sep 28  2022 usdoi.txt
theia@theia-lemai0509200:/home/project$ chmod o-r usdoi.txt
theia@theia-lemai0509200:/home/project$ ls -l usdoi.txt
-rw-r----- 1 theia users 8121 Sep 28  2022 usdoi.txt
```
* Ex2: Understanding directory access permissions

2.1 View default directory access permissions
```
theia@theia-lemai0509200:/home/project$ mkdir test
theia@theia-lemai0509200:/home/project$ ls -l
total 16
drwxr-sr-x 2 theia users 4096 Sep  6 21:43 scripts
drwxr-sr-x 2 theia users 4096 Sep  6 22:20 test
-rw-r----- 1 theia users 8121 Sep 28  2022 usdoi.txt
theia@theia-lemai0509200:/home/project$ cd test
theia@theia-lemai0509200:/home/project/test$ mkdir test2
theia@theia-lemai0509200:/home/project/test$ cd ../
theia@theia-lemai0509200:/home/project$ 
```
2.2 Remove user execute permissions on your `test` directory
```
theia@theia-lemai0509200:/home/project/test$ cd ../
theia@theia-lemai0509200:/home/project$ chmod u-x test
theia@theia-lemai0509200:/home/project$ cd test
bash: cd: test: Permission denied
theia@theia-lemai0509200:/home/project$ ls -l
total 16
drwxr-sr-x 2 theia users 4096 Sep  6 21:43 scripts
drw-r-sr-x 3 theia users 4096 Sep  6 22:22 test
-rw-r----- 1 theia users 8121 Sep 28  2022 usdoi.txt
theia@theia-lemai0509200:/home/project$ mkdir test/test3
mkdir: cannot create directory ‘test/test3’: Permission denied
theia@theia-lemai0509200:/home/project$ chmod u+x test
theia@theia-lemai0509200:/home/project$ chmod u-w test
theia@theia-lemai0509200:/home/project$ ls -l
total 16
drwxr-sr-x 2 theia users 4096 Sep  6 21:43 scripts
dr-xr-sr-x 3 theia users 4096 Sep  6 22:22 test
-rw-r----- 1 theia users 8121 Sep 28  2022 usdoi.txt
theia@theia-lemai0509200:/home/project$ cd test
theia@theia-lemai0509200:/home/project/test$ mkdir test_again
mkdir: cannot create directory ‘test_again’: Permission denied
theia@theia-lemai0509200:/home/project/test$ 
```
* Practice exercises

1. List the permissions set for the file `usdoi.txt` that you downloaded to your project directory at the beginning of the lab.
```
theia@theia-lemai0509200:/home/project$ ls -l usdoi.txt
-rw-r----- 1 theia users 8121 Sep 28  2022 usdoi.txt
```
2. Revoke the write permission on `usdoi.txt` for the user, and verify your result.
```
theia@theia-lemai0509200:/home/project$ chmod u-w usdoi.txt
theia@theia-lemai0509200:/home/project$ ls -l usdoi.txt
-r--r----- 1 theia users 8121 Sep 28  2022 usdoi.txt
```
3. What happens if you try to delete `usdoi.txt` after revoking write permissions for the user?
```
theia@theia-lemai0509200:/home/project$ rm usdoi.txt
rm: remove write-protected regular file 'usdoi.txt'? y
theia@theia-lemai0509200:/home/project$ ls usdoi.txt
ls: cannot access 'usdoi.txt': No such file or directory
```
4. Create a new directory called `tmp_dir` in your home directory.
```
theia@theia-lemai0509200:~$ mkdir tmp_dir
theia@theia-lemai0509200:~$ ls
docker-compose         package.json                         tmp
dsdriver               plugins                              tmp_dir
entrypoint.sh          postgres                             user-info.txt
gen-webpack.config.js  README.md                            users.txt
javasharedresources    report.sh                            webpack.config.js
lib                    skills-network-extension-v0.1.0.tgz  yarn.lock
node_modules           src-gen
```
5.  View the permissions of the newly created directory, `tmp_dir`
```
theia@theia-lemai0509200:~$ ls -ld tmp_dir
drwxr-xr-x 2 theia theia 4096 Sep  6 22:45 tmp_dir
```
6.  Revoke the user write permission for `tmp_dir`
```
theia@theia-lemai0509200:~$ chmod u-w tmp_dir
theia@theia-lemai0509200:~$ ls -ld tmp_dir
dr-xr-xr-x 2 theia theia 4096 Sep  6 22:45 tmp_dir
```
7.  Check whether you can create a subdirectory of `tmp_dir` called `sub_dir`.
```
theia@theia-lemai0509200:~$ cd tmp_dir
theia@theia-lemai0509200:~/tmp_dir$ mkdir sub_dir
mkdir: cannot create directory ‘sub_dir’: Permission denied
```