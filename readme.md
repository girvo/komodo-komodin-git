Use this extension on Linux or Mac to add Git commands to Komodo.

Introduction:

<blockquote>
I'm new to Linux, Git, Komodo and extensions. 

I were using Dreamweaver on WinXP and TortoiseGit. Since my switch to Linux I'm using Komodo Edit and I missed Git integration (<em><a href="http://www.activestate.com/komodo-ide/features">Komodo IDE</a> provides Git integration and a lot of more features</em>).
 I have some experience with Mozilla Extensions then I decided to add this. If you see some bug please let me know.
</blockquote>

Usage:

<blockquote>
Right click on multiple/single files/folders of the "places" sidebar, or from the toolbarbutton to apply commands to focused document. There is also a git submenu on document and tab context menu.

</blockquote><br/>

Available commands:
<pre>
      Add & Commit
          o git add "/selected/paths/files/or/and/folders"
          o git commit "/selected/paths/files/or/and/folders" -m "promptMessage"
      Add & Commit & Push
          o git add "/selected/paths/files/or/and/folders"
          o git commit "/selected/paths/files/or/and/folders" -m "promptMessage"
          o git push

      Commit
          o git commit "/selected/paths/files/or/and/folders" -m "promptMessage"
      Commit Amend
          o git commit "/selected/paths/files/or/and/folders" --amend -C HEAD
		  
      Commit All
          o git commit -a -m "promptMessage"
		  
      Diff
          o git diff "/selected/paths/files/or/and/folders"
      Status
          o git status "/selected/paths/files/or/and/folders"

      Log
          o git log --stat --graph --date-order "/selected/paths/files/or/and/folders"   
      Log ( Extended )
          o git log -p "/selected/paths/files/or/and/folders"
      Blame
          o git blame "/selected/paths/files/NOT/folders"

      Revert
          o git checkout -- "/selected/paths/files/or/and/folders"
      Revert & Clean
          o git checkout -- "/selected/paths/files/or/and/folders"
          o git clean "/selected/paths/files/or/and/folders" -f -d

      Revert to object
          o git revert promptMessage
      Checkout to object
          o git checkout promptMessage

      Push
          o git push
      Pull
          o git pull

      Add
          o git add "/selected/paths/files/or/and/folders"
      Remove
          o git rm "/selected/paths/files/or/and/folders"
		  
      Init
          o git init
      Clone
          o git clone promptMessage

      Add to Git Ignore
      Open Git Ignore
	  
	  Liberal Git Command
</pre>

Internals:
<blockquote>
To execute a Git command this add-on creates temporal shell scripts. On my fedora installation these are under /tmp/kGit/kGit-[1-n].sh

The add-on runs the scripts asynchronously /bin/sh "/tmp/kGit/kGit-[1-n].sh".

The output is redirected to "/tmp/kGit/kGit-[1-n].diff" and "on command complete" the file is opened in a new komodo tab, which shows the output with pretty colours.
</blockquote><br/>

License:<br/>
GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007

Todo:<br/>
http://github.com/titoBouzout/komodin--Komodo-Edit-Git-/blob/master/todo.txt

Know Bugs:<br/>
A commit is sent for each selected file, it should do: one commit for all selected files for each repository.

Source-Code:<br/>
http://github.com/titoBouzout/komodin--Komodo-Edit-Git-

Current Version Changes:

  <ul>
  <li>
	<b>1.101027.1</b> - http://community.activestate.com/files/kGit_1.xpi
	<ul>
	  <li>Fixes:
	  <ul>
		<li>Properly manages directory and file names by using paths instead of file:// URIs.
		<li>Ask for confirmation on sensible commands.
	  </ul>
	  <li>Improves:
	  <ul>
		<li>log shown as graph in date order.
		<li>Changes git log to git log --stat, to display a little more of information.
		<li>Adds "Open Git Ignore"
		<li>Adds "Add to Git Ignore"
		<li>Adds "Log (extended).
		<li>Adds "Blame" command.
	  </ul>
	</ul>
  </li>
  </ul>

All versions Changes:<br/>
http://github.com/titoBouzout/komodin--Komodo-Edit-Git-/blob/master/changes.html
