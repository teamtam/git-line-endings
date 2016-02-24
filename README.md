# git-line-endings

This sandbox contains files with various line ending formats (LF, CRLF, mixed) to explore the effect of using Git to normalize line endings in `.gitattributes`.

Below are steps you can take to see this for yourself. It assumes you are on a Windows machine.

    git clone https://github.com/teamtam/git-line-endings.git
    cd git-line-endings
    git checkout -b test

At this point, you can use your preferred text editor (e.g. Notepad++) to verify the line ending format is as expected in each file. Also, verify that line 4 of *.gitattributes* is set to `* -text`.

Change line 4 of *.gitattributes* to: `* text=auto` 

    git add .gitattributes
    git commit -m "Changed .gitattributes to normalise line endings"

Add some changes to *Unix.txt*, *Windows.txt*, *Mixed.txt*

    git add *.txt
    git commit -m "Let's see what happens to line endings"

However, you won't see anything noticable changes until you force your working directory to update.

    git rm --cached -r .
    git reset --hard (to update working directory)

At this point, you should see all 3 files now consistently have Windows format line endings (CRLF).
