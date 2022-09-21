# tdr ![linux](https://github.com/plicease/App-tdr/workflows/linux/badge.svg)

Legacy Test Driver

# SYNOPSIS

**tdr** \[-v  \[-i\] \] \[-o\] `cmd` \[`args`\]

# DESCRIPTION

tdr is a program for testing programs.  tdr executes `cmd` and puts the
various standard streams in the appropriate places.  `cmd` is intended to
be a here document with a .t extension.  If the extension exists, then
this part of the file name will be removed for the output streams.  If
there are expected output files present in the current directory, then tdr
will do a **diff**(1) on the expected and actually output and inform the
user that differences were found. 

# FILES

all these files should be found in the current directory the test program
is named **fred** or **fred.t** in this case: 

## GENERATED FILES

```
fred.ao      - actual output created by tdr
fred.aERR    - actual error stream created by tdr
fred.diff    - differences (ie. unix diff) between actual and expected
               output iff there is a difference
fred.diffERR - differences between actual and expected error stream
fred.aRET    - text file with the return value
tdr.log      - log file for the test driver.  this file is appended to.
```

## EXISTING FILES

```
fred.eo      - expected output created by programmer
fred.eERR    - expected error stream created by programmer
fred.eRET    - expected return value
```

note that the diff files are only created if there is a difference.  the
program warns the user when a file is to be overwritten if -v option used
but doesn't prompt, unless the -i option is specified.  

# OPTIONS

```
-v      warn before over writing files.
-i      prompt before over writing files.
-o      do not overwrite log file.
```

# RETURN VALUES 

```perl
0 - normal execution 
1 - user abort 
2 - usage line 
3 - file doesn't exist
4 - difference between actual and expected output
```

# SEE ALSO

**diff**(1)

# CAVEATS

This is a legacy test driver and shouldn't be used for any new projects.

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 1996 by Regents of University of California.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
