The **apply-patch-to-file** script allows you to apply a Git patch to files with the same content but different name or file path without having to manually modify the patch itself.

Instructions
------------

Use with the following syntax:

    apply-patch-to-file [-i] [-a <arguments_for_git_am>] <patch>
                        [-f <file_to_patch>] [-a <arguments_for_git_am>] <patch>
                        [-h]

Not specifying any options defaults to interactive mode.

Options
-------

* **-f** *file_to_patch* — allows you to specify a single file that will be patched. This means that the specified patch must only modify one file.
* **-i** — starts your favorite editor with a pre-formatted table in which you specify target files that will be patched.
* **-a** *arguments_for_git_am* — allows for arguments to be passed through to the git am command that applies the patch. If multiple arguments are desired, they should be written in quotes like, "--ignore-whitespace --ignore-space-change"
* **-h** — displays usage information.

Example
-------

1. Create a patch of, for example, the HEAD commit in your Git repository:

        repo1]$ git format-patch HEAD^

2. Switch to a different repository in which you'd like to apply the patch to a file or files of your choosing, and run **apply-patch-to-file** script, specifying the previously-created patch as an argument:

        repo2]$ apply-patch-to-file -i ~/patches/0001-my-test-commit.patch

3. In your editor, specify the target files where the patch should apply:

        File Specified in Patch   Target File
        -----------------------   -----------
        test/blue.xml             test/red.xml
        images/hello.sh           test/images/hi.sh

4. Save and exit you editor. In case of no conflicts, check **git log** to see your patch applied.

Copyright
---------

apply-patch-to-file — . Copyright (C) 2012 Martin Prpič

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see [http://www.gnu.org/licenses/](http://www.gnu.org/licenses/).
