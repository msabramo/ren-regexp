A copy of Michael Forman's awesome "ren-regexp" mass rename utility, since [his
web site](http://www.michael-forman.com/perl/ren-regexp.html) ([archive.org
version]http://replay.waybackmachine.org/20090223051758/http://michael-forman.com/perl/ren-regexp.html())
seems to have disappeared and finding recent versions of the program seems
difficult now.

ren-regexp applies one or more regular expressions to a list of file names.
This provides a method of applying common modifications to many files that
would otherwise require repetitive, atomic file operations.

    NAME
        ren-regexp - Rename files by the application of regular expressions
    
    SYNOPSIS
        ren-regexp [ -dhtv ] [ -cfgiqu ] [*regexp ...*] ([*pattern ...*])
        ([*file ...*])
    
    DESCRIPTION
        ren-regexp applies one or more regular expressions to a list of file
        names. This provides a method of applying common modifications to many
        files that would otherwise require repetitive, atomic file operations.
    
    OPTIONS
        -c --color
    
        -u --underline
    
        The "--color" and "--underline" options can be used together or
        separately to highlight changes in the filename as the regular
        expression are applied.
    
        -d --debug
    
        Print additional information useful for debugging.
    
        -f --force
    
        If the new file exists, this will force an overwrite.
    
        -g --global
    
        Apply all regular expressions globally to a filename. This is equivalent
        to appending a "*g*" to the end of all regular expression as in
        "*s/regexp/string/g*".
    
        -h --help
    
        Prints this information.
    
        -i --insensitive
    
        Apply all regular epxression without sensitivity to case. This is
        equivalent to appending an "*i*" to the end of all regular expression as
        in "*s/regexp/string/i*".
    
        -q --quiet
    
        ren-regexp is rather verbose for a unix program. Consider this a feature
        to prevent data loss. To keep things quiet, use this option.
    
        -t --test
    
        Test the application of the regular expressions without renaming the
        files. This is highly recommended to prevent the loss of data.
    
    PATTERNS
        In addition to passing a list of files to the program by using shell
        globs, one can also use regular-expression matching to select files from
        the working directory or to filter a list of files and directories
        included on the command line.
    
        The following example shows the standard use of shell globs.
    
        ren-regexp 's/tiff$/.tif/' *tiff
    
        The following example shows the use of regular-expression pattern
        matching.
    
        ren-regexp 's/tiff$/.tif/' /tiff/
    
        The following example shows the combination of regular-expression
        pattern matching used to filter shell globs..
    
        ren-regexp 's/tiff$/.tif/' /vacation/i *tiff
    
    EXAMPLE
        The following example shows standard usage. The regular expression,
        "*s/.mp3/ of 3.mp3/*", is applied to the three files resulting in files
        matching the pattern "*PI-01 of 3.mp3*".
    
        ren-regexp "s/.mp3/ of 3.mp3/" PI-01.mp3 PI-02.mp3 PI-03.mp3
    
        The following examples all have the same result. Note that the initial
        "*s/*" are both optional with the final "*/*" option if there is no
        modifier.
    
        ren-regexp "s/A/B/i" *
    
        ren-regexp -i "s/A/B/" *
    
        ren-regexp "A/B/i" *
    
        ren-regexp -i "A/B" *
    
        The following example shows three regular expressions applied in turn on
        a filename. The file progresses from the original of "*ABCD.txt*" to
        "*abCD.txt*", "*ABcD.txt*", and finally "*AcDB.txt*". The single quote
        is necessary to prevent the shell from expanding the regular expression
        variables, "*$1*" and "*$2*".
    
        ren-regexp "AB/ab" "abC/ABc" '(B)(cD)/$2$1' ABCD.txt
    
    BUGS
        The color ouput doesn't like regular expressions variables (i.e.,
        "*$1*").
    
    SEE ALSO
        mv
    
    AUTHOR AND COPYRIGHT
        Michael Forman <Michael.Forman@Colorado.EDU>
        http://www.Michael-Forman.com
    
        Copyright (C) 2005 Michael Forman. All rights reserved. This program is
        free software; you can redistribute it and/or modify it under the same
        terms as Perl itself. Please see the Perl Artistic License.
