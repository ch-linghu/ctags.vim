ctags.vim
=========

the mirror of http://www.vim.org/scripts/script.php?script_id=610


description
-----------

This is a new version of Alexey Marinichev's ctags.vim script, vimscript #12. I have modified it with the author's permission, but cannot upload it as a new version of the original script because Vim Online now allows only the original author to do that. 


The original script used exuberant ctags to build a list of tags for the current file and displayed the name of the function the cursor was in (actually the name of the tag at or above the cursor's line) in the title bar. 


This version has been modified to display the function/tag name in the status line instead of or in addtion to the title bar.  If multiple windows are open, the correct function/tag name is displayed in each status line. The script has also been modified to be a plugin instead of having to be sourced. Finally, since exuberant ctags now supports Python and Vim languages as well as C, .py and .vim were added to the list of suffixes that automatically start the script. 


New in Version 2.1 
-------------------

1.  Keith Reynolds contributed some changes that have made a dramatic improvement in the startup time when opening large files containing many tags.  The improvement is greatest when using a vim compiled with Perl support.  His changes also result in this version using less memory than version 2.0. 

2.  Keith also added automatic enabling of the status line (i.e., setting 'statusline' to 2) when entering a buffer in which the script is active. 

3.  The default g:ctags_args value has been changed to use C and vim type values more appropriate for this plugin.  If you prefer the previous defaults, the values are still noted in the script and can be used instead by setting them yourself in your ~/.vimrc. 

4.  The default g:ctags_path value has been changed to be better for most users.  This can also be reverted to the previous default value by looking in the script for the previous setting and putting this in your ~/.vimrc. 

5.  The ctags database is now regenerated every time a buffer is saved.  This keeps the database up to date as a file is changed.  If this is a performance problem for you, just add 

        let g:ctags_regenerate = 0 

to your ~/.vimrc. 

6.  The behavior of the cursor when moving vertically through text has been improved.  It no longer "forgets" the column to which it was last set as often.  It may forget now only when the tag name changes. 

7.  Configuration varaibles may now be set at any time, not just at vim startup time. 
 
install details
Copy ctags.vim to your plugin directory. 

If the ctags program is not in your PATH, you will need to add the following to your vimrc: 

    let g:ctags_path=<path to your ctags> 

and to enable the display of function names in the status line, you will need to add this: 

    let g:ctags_statusline=1 

Other configuration variables you may want to change are: 

    g:ctags_args 
        Additional arguments to the ctags program. 

    g:ctags_title 
        Set to 1 if you want the function name also displayed in the title bar. 
        This is the default, but if g:ctags_statusline is set to 1, this must also be 
        set to one to show the function name in the title bar. Otherwise, the 
        function name appears only in the status line. 

    generate_tags 
        Set to 1 if you want the script to be started automatically for the supported 
        file types (actually file extensions). Otherwise the script must be started 
        manually with the CTAGS command. 

    g:ctags_regenerate 
        Set to 0 if you don't want the tags database rebuilt each time 
        the buffer is written.
 
