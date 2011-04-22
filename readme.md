Adds Git commands to Komodo Edit and enhance Git commands on Komodo IDE. Also adds icons overlay to Komodo Edit.
<img src="http://dl.dropbox.com/u/9303546/komodo/kGit/screenshot.png" style="float:right"/>

Usage:

<blockquote>
Right click on multiple/single files/folders of the "places" sidebar to apply commands on selected files.

To apply commands to focused document use the toolbarbutton. There is also a git submenu on document and tab context menu.

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
Undo Last Commit
  o git reset --soft HEAD^
  
Diff
  o git diff "/selected/paths/files/or/and/folders"
Status
  o git status --untracked-files=all "/selected/paths/files/or/and/folders"

Log
  o git log --stat --graph --date-order "/selected/paths/files/or/and/folders"   
Log ( Extended )
  o git log -p "/selected/paths/files/or/and/folders" -n 30
Log ( Full )
  o git log -p "/selected/paths/files/or/and/folders"
Blame
  o git blame "/selected/paths/files/NOT/folders"

Revert
  o git checkout -- "/selected/paths/files/or/and/folders"
Revert & Clean
  o git checkout -- "/selected/paths/files/or/and/folders"
  o git clean "/selected/paths/files/or/and/folders" -f -d
Checkout Files To object
  o git checkout promptMessage "/selected/paths/files/or/and/folders"

Revert to object
  o git revert promptMessage
Checkout to object
  o git checkout promptMessage

Push
  o git push
  
Pull
  o git pull
Fetch
  o git fetch

Add
  o git add "/selected/paths/files/or/and/folders"
Remove
  o git rm -r -f "/selected/paths/files/or/and/folders"
Remove Keep Local
  o git rm -r --cached "/selected/paths/files/or/and/folders"
  
Init
  o git init
Clone
  o git clone promptMessage

Add to Git Ignore
Open Git Ignore

Git GUI
Gitk
Liberal Git Command
</pre>

Enabling Icons Overlay (KOMODO EDIT ONLY!!!!):
Properly formated explanation at : http://community.activestate.com/xpi/komodin-git-places 

<blockquote>
Locate and Backup the file: /ActiveState Komodo Edit 6/lib/mozilla/extensions/places@activestate.com/components/koPlaceTreeView.py

Backup!

Ok, now open the file and make the following changes:

Under "import uriparse"
Write: "import hashlib"

Should be:
"
...
import uriparse
import hashlib
...
"

Then locate the function "_buildCellProperties" and replace it with :
NOTE: KOMODO EDIT ONLY!!
<python>
    def _buildCellProperties(self, rowNode):
        properties = []
        if not self.safe_isLocal():
            return properties
        koFileObject = rowNode.koFile
        if not koFileObject:
            return properties
        koFileObject = UnwrapObject(koFileObject)
        m = hashlib.md5()
        m.update(koFileObject.path.replace('\\', '/'))
        properties.append('k'+m.hexdigest())#the css selector need start with a letter
        if koFileObject.isReadOnly:
            properties.append("isReadOnly")

        return properties
</python>

Start and close komodo two times..

If the places sidebar is not loading, look if there is a syntax error into the file. ( "Tabs at the begging of each line should be spaces" )

Done!

NOTE: If there is some error just restore your backup and restart komodo two times.

NOTES:
 - Unmodified files will shows as is ( normal komodo icons )
 - The "look for changes" executes every 7 seconds.
 
</blockquote>

Internals:
<blockquote>
To execute a Git command this add-on creates temporal shell scripts. On my fedora installation these are under /tmp/kGit/kGit-[1-n].sh

The add-on runs the scripts asynchronously /bin/sh "/tmp/kGit/kGit-[1-n].sh".

The output is redirected to "/tmp/kGit/kGit-[1-n].diff" and "on command complete" the file is opened in a new komodo tab, which shows the output with pretty colors.
</blockquote><br/>

License:<br/>
GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007

Todo & know bugs:<br/>
https://github.com/titoBouzout/komodin--Komodo-Edit-Git-/blob/master/todo.txt

Source-Code:<br/>
https://github.com/titoBouzout/komodin--Komodo-Edit-Git-

All versions Changes:<br/>
https://github.com/titoBouzout/komodin--Komodo-Edit-Git-/blob/master/changes.html

Changes From Latest Version:

<ul>
  
  <li>
	<b>1.110422.10</b> - http://community.activestate.com/files/kGit_7.xpi
	<ul>
	  <li>Fix:
	  <ul>
		<li>Ignored files take preferences (on icons) over untracked files.
	  </ul>
	</ul>
  </li>
	    
  <li>
	<b>1.110421.9</b> - http://community.activestate.com/files/kGit_6.xpi
	<ul>
	  <li>Fix:
	  <ul>
		<li>Directories with special characters now show icons properly
	  </ul>
	  <li>Improves:
	  <ul>
		<li>Show icons for all the repositories under the current places sidebar
		<li>Renames icons to short CSS size.
	  </ul>
	</ul>
  </li>

</ul>