trello_backup
=============

A Perl script to backup (in "diffable JSON") the contents of your Trello
private (not public!) boards.

Prerequisites
=============

* Perl, recent-ish
* A few Perl modules, installable via:

    cpanm LWP::UserAgent Config:INI::Reader JSON::Diffable File::Slurp

Configuration
=============

First, configure the script by requesting your key and secret:

* go to https://trello.com/app-key
* note down the `key` and `secret`
* `cp config.ini.sample config.ini`
* edit `config.ini` and substitute the correct values in that file
* run `./bin/trello_backup_request`
  * follow the URL and authorize the applicaton. You'll be given a code.
  * Insert the code where the application requests for it.
* ln -s ..../bin/trello_backup ~/bin/

Usage
=====

Once configured, simply run:

    .../bin/trello_backup

or, if you've symlinked to your `~/bin/` directory,

    trello_backup

You could even stick it in `cron`.

Your (diffable) JSON files will then appear in the repo's `backups` directory.

Keeping track of your backup
============================

You can easily create a Git repository inside `backups/`, and since the JSON
generated is diffable, only very small changes are going to get saved to the
repository at every backup: just the changes that have actually happened!

LICENSE
=======

This is Free Software. You can redistribute it and/or modify it under the terms
of either The GNU General Public License[1], as published by the Free Software
Foundation[2], Version 1 or any later version[3], or The Artistic License[4].

[1]: http://dev.perl.org/licenses/gpl1.html
[2]: http://www.fsf.org/
[3]: http://www.fsf.org/licenses/licenses.html#GNUGPL
[4]: http://dev.perl.org/licenses/artistic.html
