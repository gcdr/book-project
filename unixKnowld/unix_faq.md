


15) tail -f /var/log/apache/sue...SU....

16) to capture your STDERR, to a file.
	command 2> thefile.log
	command 2>/dev/null

17) job control.
	a) You cannot logout - stranded jobs & expect to re-attach to them, later.
	jobs: shows what you have pending.
	fg 1: will bring job 1, into you shell.

18) sort +0 -b -g (g for numbers).
	sort -u # unique, remove dups.
	sort -r # reverse.
	sort -o output.txt input.txt
	sort names | uniq -d # show just dups. (Have to sort, for uniq to work.)
	sort names | uniq -c # show counts, with normal output.
	egrep -v '^@' hiss_2_0013.gram | uniq | less

19) card sort [--command="cc -flags"] -Pdisplay -ocardit.ps

20) c2ps -2 -p Letter aprg.cpp >aprg.ps
    ps2pdf -sPAPERSIZE=letter aprg.ps
	ps2ascii input.ps >output.txt

	c2ps -t 4 -1 -p Letter aprg.cpp >aprg.ps
	pstops "2:0L@.7(21cm,0)+1L@.7(21cm,13.2cm)" input.ps >output.ps

21) c2ps -d 0 -C Palatino-Italic 

22) c2ps -p Letter infile.c > outfile.ps
	bcpp -cc 10 -bcl -s infile.c outfile.c2

23) touch -d 01/15/2001 afile.name
	touch -t 2001 01 15 1735. 47 afile.name # this has ADDED spaces...
	touch -t 01151830 afilename # normal plain mandatory format.
		200101151735.47
	date -s'2002/04/07 01:30:0'	

24) global replace for vi.
	:%s/
		\.\/
		/
		grep -i -l list \.\/
	/g

OR start with %s///g - then fill in the pieces.

25) DOING //! hidden comments removal. Use vim.
%s///g
	\/\/!.*     the other leave blank

26) fmt -30 input.file > output.file
	formatter - re-forms to 30 char long word-wrapped lines.

27) astyle --indent=tab=2 --style=gnu -S -C input.file > out.file

28) Goliath latex symbols:
	/usr/share/texmf/tex/latex/amsfonts
	/usr/share/texmf/tex/latex/base/book.sty
	/usr/lib/latex2html/icons.gif (icons for it).

	FreeBSD: /usr/local/share/texmf/tex

28B) The plain command from NDSU
    latex2html -no_subdir -info "" -bottom_navigation -t "Astronomy Speech" tz_06.latex

29) vi macro (vi commands)
	and vi abbreviations
:map swap xph
:umap swap // to clear it

:map hot itypeit<CTRL-v><hit ESC key>

:ab sym1 $\blacktriangle$
:unu sym1

	vi -s abs03.txt inputFile.txt

30)
  egrep '' ``
  egrep 'keyword' `find . -type f -print`

  (xarg form) find . -type f -print | xargs 'keyword' /dev/null

  (one file lister) 
  grep "whatever" /dev/null ./*.cpp

  egrep -i "'[a-zA-Z0-9]*'" ui_83.txt # egrep with ' apos in string, must use " quotes.

31) complex compile & linking.
	g++ -o thread3 -lpthread a_thread_program.cpp
	(-lg++ used for some??? c++ programs)
	
	g++ -Wall typ02.cpp >ttt02.err 2>&1 # for capturing those hard to get streams!

32) (if allowed) lpr -Plw150b-1 -#3 threecopy.ps

33) vi macro library:
  map ho
	0i\section}^[
	A}^[
	oDescribe:^[
	o//^[
	o^[j
  # creates 3 line expansion. would be nice to find a easier text to leave
insert mode.

  map hu
	^[

  map ho: # Standard Dup Line (with ls).
    yypkAy<Esc>:.,j<Enter>j

34) a2ps --list=defaults.
	a2ps --medium=Letter -o fam.ps fam.txt

35) as root: /sbin/hdparm -Tt /dev/hda1

36) netstat -a
	netstat -n | head -20 # Interesting.
    netstat -a -b # Revealing on Windows; runs a while though.

37) dict anonymity

38) /sbin/init.d/rc2.d
	versus inetd.conf

39) write nichols<>
	a line
	a line<Ctrl-D>

	wall<>
	a line
	a line<Crtl-D>

40) cmp, diff, sdiff

41) ignorecase searching in vim.
	:set ic
	:set noic (to reset)
	/time_t (can be used).

42) grep -i -l -d recurse keyword *.h
	grep -A 10 -B 2 ^class *.h | less # Useful for seeing lines before and after.
	A CASE OF CONTRASTING REGULAR LOGIC:
	find . -name '*.c*' -print | grep -v '\.c[~p]' | grep -v '\.c$' | less
		* show all *.c* files
		* remove .cpp
		* remove .c[END OF LINE marker].

	du -ach . | grep ^.[\.].M # find 100M and up.
	du -ach . | grep ^.[\.]M # find 10M and up.

43) vi search,prompt,replace
  0,$s///gc
	0,$///g # Just do-it!

44) /usr/sbin/tcpdump port 10000
	as root

45) Unusual personal files:
	.signature, .plan, .profile

46) bwyman option works in top.
	* a ssh_get, ssh_add; can auto work with rlogin - similar functionality.
	* ~ in vi - switch case.
	* syntax=on, xterm:color

47) The troubling sticky bit.
	chmod 745, g+x, g+s
	# For linux, proper way to set sticky bit on /tmp dir.
	chmod +t tmp # in / (root).
	# Meaning on directories, is about any user's usage of text files.
	# Versus, on files, about keeping the executable image in memory, for faster loading.

48) The command line calculator:
	bc -l
	to leave: quit

49) mount -t msdos /dev/hda5 /dos16
	mkdir /dos16 (from /).

50) the magical - join line command in vi!!!
	-,.j<>   $bhx  (or .,+j<>)

51) I don't know the exact requirements on the server - roboto.
	But, on the client - before you log onto roboto, you have to do a xhost +134.129.61.163.
	Also, using xhost - seems to be - only active during running X session. Also, X needs to be running to connect to the Xserver. (that is simple enough).

52) man printcap | col -b
	man -t ls | lpr -Pmutt@lw150b-1 # Makes a very nice and fancy man page printout.
	cat ppp_command.4 | nroff -man | less # Note, cannot be gzip form.
	cat -v . | strings | less # show dir, crude on BSD only (Linux SysV).

53) pstree -ap 
    pstree -Gap | more # less bad. (For funky Unix systems.)
	strace -p PID (ie. 1533).

54) ln -s ~/vent/tex3 linktex3
	ln -sf realFile theLINK!!!

55) C++ formatting programs.
	indent
	c++2latex (tex)
	tgrind (tex)

56) Secret to vim named buffers, use the " before the letter name for the buffer.
	Such as "ayy, puts a yanked line into buffer a.

57) The elusive - fix the dumb linefeeds from MS-DOS files. (dos2unix didn't work.)
	tr -cd '\11\12\40-\176' <main.latex >main2.latex
	perl -pe -i.lfcr "s/[\012\015]//;" file # For DOS to Unix.
	perl -pe -i.lf "s/[\012]//;" file # For Unix to DOS.

	# I had to use it WITHOUT the -i option and, > afile.output.

	# An alternative? with col cmd.
	col -bx < infile > outfile

	# vim command all uppercase letters, to lowercase.
	:%s/[A-Z]/\L&/g
	:%s[a-z]/\U&/g # The other way.

58) fmt -w 75 input.txt >output.txt :to format a paper for typical typing lines.
    par # Another useful paragraph formatting program.

59) cut --b=31-47 afile >afile.ver2 :to cut only wanted char-columns from a file into another. (paste can be used, too. later).
	ls -l | cut --b=55-100 > fil1.sh
	ls | paste #But then includes DIRS - whatever.
Clever way to delete all but specified wildcard files.
	ls | paste - | grep -v \.ps | xargs rm /dev/null
	cut --b=30- afile # The - hyphen here indicates to EOL end of line.
	ls -latr --color=never --full-time

60) card cut --command="cc -flags" "-2 --medium=Letter" -ocut_card.ps
	Not a perfect solution - to formatting a reference card to Letter sized paper, but the fault is in card - since it calls a2ps automagically - when it sees a single dash '-' unknown parm - unfortunately they forgot about -- doubles. And thus, if card calls a2ps; you can't help it being this way.
	a) Unless, you rebuild a2ps for its own default of Letter. (Or perhaps a configuration files - could do that without re-building the thing.)
	b) Also, if you can find how to grab its - goes to lpr (or lp) command without having it auto-dump it to a printer - then perhaps I can personally handle it better.

61) category commands:
	xpdf, acroread
	gdb, kdb, ddd, (vdb), (kdbt), xxgdb (what?)
	gv, ghostview (a viewer), gs (is gs_x11) (prg to convert ps to non-ps).
	gimp
	vi, elvis, vim, gvim
		emacs, aedit, mcedit (also mc), bedit, gedit, pico (Sarah's), jed, jove 

	vi, vim: is best for works everywhere. (Can run even on a floppy only system.)
	emacs: is best for has high-end programmability (EmacsLisp) but takes lots of power.

	pine, elm, mutt, 'sendmail, 'mail, 'write,
	cal, gcal, pcal
    ical, evolution, plan, korganizer, xcal, gdeskcal, gnome-pim?, xf (XF?)calendar, konsolekalendar
    -- mozilla (view calendar).
    # Cosmo Clients: 
    chandler, evolution, sunbird, lightning?

	awk, gawk, perl, sed,
	grep, egrep, fgrep, --- agrep, ngrep, zgrep, zipgrep, pgrep, rgrep
	sgrep (structured grep)
	mswordview (v8/97), word2x (v6), ispell
	diff, sdiff (screen), wdiff (words), zdiff (compressed), pdiff (pretty.), cmp
		xwdiff (X-based).
	tr, recode
	scp, rsync (not secure), rcp (insecure)
	cut, paste, split, tee, tail, head, 
    fmt, par
	/dev/null, 2>,
	astyle, bcpp, c2ps

	a2ps, html2ps, ps2pdf, latex2html, enscript ALSO: mf, mft, mpost, weave (METAFONT, MPOST), tangle, web2c, pc, pxp (pascal coding). makempx (part of mpost).
	xdos, x128, x64, z81
	zip, unzip, unrar, shar, unshar
	tar .tar, .tarZ, lharc?, gzip?
	xscheme, gforth, xlisp, zoo
	tcsh, bash, csh, sh, zsh, ypsh, ???
	m4: Macro Processor (shell script inside a shell).

	gimp, imageMagik, xv (xView)
	gnumeric, (AND) sc [textual spreadsheet calculator, looks like DOS 1-2-3ish.], psc is a utility for it.
	sort, tsort

	grok # A cardfile paradigm form database handling of fielded strings, Unix Program.

	sq (squeeze), look (lines starting), join.
	elisp: LISP in Xemacs.

	Office Suites: siag (usu. w/ kde), koffice, star office, abi-word, 602 Office (win only?).
	dmesg: show boot messages

	gperf: generate perfect hash tables?
	ptx: make permuted index(es). (gptx) info ptx.

	xearth, xmars, xsnow, xmoon, XEphem, xplanet !
	we: Windows X Environment. # Interesting file manager?
    gnuchess, glchess (X-based).
    Browsers: mozilla, firefox, netscape, lynx, w3m, opera, jakarta?

62) ls | paste - - -  // show in 3 columns.
	paste -d"\n" file1.txt file2.txt     // the cross-merge 2 files solution.
	ls | paste -d" " -
	paste -s -d"\t\n" file   // combine pairs of lines from a file, into 1 line

	ls | columns #shows as up-down columned.
	pushd ., popd, dirs, dirs -v, more -l ????, cd - (works too).
	cd - # is a ROTATE among the dirs version!

	paste -s - # tab assumed by default, in 'cut ', too.
	paste -d' ' -s -

63) hexdump -x afile.txt (shows hexadecimal values)
		od is obsolete. hexdump -xc shows characters - however, the chars are not aligned with the numberings. Should find a better thing - in the future.
		hexdump -cb file # nice format.

64) strings (-a) /etc | grep /
		takes any file - and only shows ascii chars, also recurse dir.s automatically.
	strings .netscape/history.dat	// rather revealing.

65) some very hard programming lore:
	no more ltoa, utoa.
	gcvt, ecvt, strtol, strtou, outdated-atoi, or atol, or atof...
So, what about a long int to a string. You aren't going to believe this. Presumably - you just simply use sprintf(). ! Which - if that is so - in C++ means use a ostrstream and copy out its buffer.

66) primes 1 200 | paste - - - -

67) dict -m (match) xat  // shows a lot of possible - sound-alike words.

68) About text editors: vi is the best for running everywhere and is lite. Can actually run from a system - off of floppies.
	However, the hard core - got to program my text editor programmer, uses       emacs. Emacs is also uses for defining editing standards for working with any specialized files types - one can make up.

70) Magic dummy IP address.
	192.168.0.99 (localhost ???)
	192.168.10.0 (local Ethernet network)
	127.0.0.0 (loopback network) [SuSE loopback] 127.0.0.1 the real localhost.

71) languages:
	ghc: Glasgow Haskel compiler
	flagship: xBase compiler (full-version commercial?) (Not OSS!)
	fpk: free Pascal compiler
	gforth: Forth
	tools for C++: doxygen, nana (documenting, logging)
	perl
	python ?
	sed, awk, gawk

72) txt2html -tf --mail -H '^ *--[\w\s]+-- *$' -a samp.foot samp.txt > samp.html


73)	A hard way - to find all 3 letter filename files - in a DIR. 2nd is best way.
     ls -l | cut --b=56-90 | grep ^...$ | paste - - - - - - 
     ls | grep ^...$ | paste - - - - - -
	 ls -d /usr/bin/???

74) A weird remote Xwindow app.
		gmc // caution: no way to turn off. Believe is gnome.

75) Getting the filespace - used by files mentioned by wildcard (in same DIR for now).
	du -ac rfc1*
	du -ach `find . -type f -print`
	du -ach `find . -name '*.pdf' -print`
	find . -maxdepth 1 -print # just files in current directory.
	ls -l `find . \! -type f -maxdepth 0 -print` | sort +4 -n
	find . \( -name '*.latex' -or -name '*.tak' \) -print # find either names.

76) Various zip formats:
	gunzip GCC.gz
	tar xvfz aTarFile.tarZ
	bunzip ???
	gzip -d aTar.tar.gz
	zip -e theFile.txt move1 (.zip) # Only top level folder.
	zip -r -e theFile.txt move1 (.zip) # Just like tar. Recurs to lower folders.

77) gv -scale -1 afile.ps

78) File DIR specifying:
	With commands that are tree sensitive? - There is a difference between 
	'*' vs '*.*' in wildcarding.

79) WinNT problems with scp.
	scp -p -r theglen@pythag:~/here/there/everywhere/* .\
To find bad-formed names.
	ls -lR >~/junk20.file  # find . -name '*\:' -print ## limitation only finds single bad-formed ESC character.
	vi junk20.file # /\\ look for the ESC.

	ls -lR /opta/theglen4/StarStuff/ | cut --b=55-100 | uniq -u >~/junk20.file
	!!! characters like: \? and \* cause special problems.

80) xroach -rc green -speed 0.5 -squish -roaches 30	
	setterm -foreground green # only console. # found under Linux- keyboard-console HOW-TO
	xnetload -if eth0 -ni -nv -u 2
	xless afile.name
	xman # allows seeing how many man pages & grouped in a certain way. categorically.
	ytree # like DOS Norton Desktop - whatever.

	ALSO: wget # common utility to do it!
	PLUS: I found numerous perl-scripts that were hacked to do it & a grepz.pl.

	wget -nc ftp://www.cran.mirrors.pair.com/bin/windows/contrib/r-release/*.zip
	wget -drc ftp://admin:passwd@www.glensite1.com
	wget -drc ftp://admin:asample@www.glensite1.com/wwwroot

    curl -O http://borkware.com/quickies/files/fullscreensaver.tar.gz
	wget -drc http://www.sampledans.com/ # Grabs whole site - if reading directories is open?
    # Using www.xxx.com/here/there/ - I believe just drops to home page, anyhow.

81)
	ftp ftp.whever
	anonymous
	iamhere@ndsu.nodak.edu

	binary
	cd pub; tex-archive; fonts; cm; mf
	prompt
	lcd tmp1 # for switching dirs on cb01.
	mget *
	reget afile_that_wasnt_complete.file # presuming original server allows.

    mget -R ./*

82) 0ddPP<esc>A_<esc)
		:.,+j<ent>0j	

83) file finding:
	find . -printf "%b " -print | grep ^0.* >~/junk20.file 
	find . \! -type d -print
	# Incremental Backups. ----------------------------
	find / -mtime -1 \! -type d -print > /tmp/filelist.daily
	find / -mtime -7 -print > /tmp/filelist.weekly
	find /tmp \! -type d -atime +3 -exec ls -l {} \;
	# the "-exec ls -l {} \;", the \; tells where the exec option is finished.
	NO GOOD? find . -type f | xargs cat {} \; >/dev/null

83B) # Applying find-exec to a whole directory set of all files.
    find . -name "*.h" -exec grep NSDoWhatIMean {} \; -print
    find . -name "*.h" -exec grep -i 'super genius' {} \; -print
    # The \; is important!

84) gcal 06/2001,07/2001,08/2001
	sed "s/ /\&nbsp;/g" junk20.html >junk21.html
	cal -y # show year.
	gcal 2003 # show year.

	# Correction for Debian gcal
	gcal --type=standard # So, normal to me. Not Deutsch.

    gcal 2 2003 # Feb. 2003
    gcal -j 2 2004 # Show day numbers
    gcal -K 2 2005 # Show week numbers
    gcal -q US_ND 3 2004 # Holidays in bold, for NDak.
    
    # Advanced pcal: PostScript calendar.
    pcal 10 2004 8 -o cal_Mar30.ps -m -f cal_Mar30
    gv -scale 0 -landscape cal_Mar30.ps

    # 1
    pcal 01 2005 4 -o cal_Jan31.ps -K -m -J -f cal_Jan31
    # 2
    pcal 01 2005 4 -o cal_Jan31.ps -n Times-Roman/12 -K -m -j -f cal_Jan31
    # 3
    pcal 01 2005 12 -o cal_Jan31.ps -n Helvetica/12 -t Times-Roman-Italic/36 -K -m -j -f cal_Jan31

85) doing info tutorial:
	h (HOME)
	b (beginning), e (end), SPACE (next), BkDel (prev), OR p & n,
	m (menu) -- notice colon mode :Foo*
	f (forward) :Link*
	d (directory) (ROOT on start), l (last),
	u (up NODE-Mode, from MENU or FORWARD),
	f C? -- to show completions.
	d mInfo -- go to start.

86) find . \( -name 'public_html' -mtime 6 \) -print 2>~/junk20.file
	ls -ld `find . -type d -print`  # show details on DIRs.
	# Only problem - don't know how to apply find on Non-DIRs.

87) Due to finding the GIF baloney!
	/etc/rc.d/rc2.d/K20apache stop # as root; to stop webserver.

88) Checking Latex steps.
	a1) That math symbols & LaTeX dir.s --- have '\ ' control-space, after them.
	a2) centerline{\Large} dir. --- for some reason needing blank-line, with '\\<nl>\ ', in order to fake-out a linefeed.

89) Little secret about root. When you need export (or setenv?) variables to come into effect. Start as normal. Put changes into ~/.bashrc. Then run (another) "bash" command. This shell will have those settings.
	rm `find . -print` (notice grave character), nice way to delete files and not directories.

	rpm -U --force --nodeps pro64-0.01-13.ia64.rpm # As root, do this to over-install something. DANGEROUS command, be advised.
	ps w, ps -A w, ps -A grep 111 # weird detailed output.

	RPM OPTIONS.
	rpm -i afile.rpm # normal usage.
	rpm -F afile.rpm # Freshen usage - what I used to update SuSE packages.
	rpm --nodeps KAI_trouble.rpm # What I used, to get KAI installed, in spite of how improperly configured.
	rpm -q afile # to query for a package
	rpm -U afile.rpm # (NOT USING - personal.) manuals say to upgrade.
	rpm -i --force afile.rpm # (a manual) says to re-install a present package, without removing and do it.

	JUNE 2002 - SuSE directed rpm (fix grade) Apache.
	rpm --nodeps -Fvh apache*.rpm mod_ssl*.rpm

90) md5sum filename, md5 filename. (Use MD5SUM!) (both do exist).

91) for x in *; do mv $x `echo $x | tr [A-Z] [a-z]`;
	a script to rename all files to LOWER-CASE form. (lower case)

	rpm -qa | grep "part_of_package_name" # to find if you have a rpm installed.
	du -b | sort +0n -r > foo-du.txt | tail # find bigfiles. (mixed results)

	du -a . | sort -rn | head -20 # 20 largest, all dirs.
	du -a `find . -type f -maxdepth 1 -print` | sort -rn | head -20 # 20 largest, 1 dir. CMD: lsBig, other lsBig any.

	apropos subject # When you know what you want, by not the command.
	apropos vt100 

	!string # re-do with that string, specific.
	!?string # re-do with any match of string.

	# how to do a concordance. and | tail # to end, for biggest results.
	cat run2.txt | tr -sc A-Za-z '\012' | sort | uniq -c | sort -n > concord.txt
	# also for all current files, start with 'cat $*'.

92) Finding hidden files.
	ls -adR | paste - | grep ^\. 
Finding backup files.
	*.*#, *.*~, *~, *.bak, *.bk1
Regex - empty line.
	^$

93) New way to do push . & popd
	Use '+' and '-'.

94) How to see the bootup screen. dmesg. (Also /var/log/boot.msg file; although not everything like dmesg.)	

95) Classic way to install Linux Apps.
	a) ./configure --prefix=/usr/special/dir/of/your/choosing
	b) make
	c) make test                make ????
	d) make install
	e) make clean (to clean or clean for re-building).

96) A magic string for NDSU's phonebook.
	http://www.ndsu.nodak.edu/phonebook/pbclient.cgi?FNAME=jo&LNAME=mu

97) A fancy ls command, shortcut invade
	ls -ltrd `find . -maxdepth 1 -perm +040 -print 2>/dev/null`

98) gcc is actually a C++ compiler, too.
	static libraries (used with linking) (.a .sa?) are included into exe file.
	dynamic shared libraries (like DLLs) .so, are not linked into. But, are callable by everyone on system and ...
****
	gcc -c square.c factorial.c
	ar r libstuff.a square.o factorial.o	# create library. If already exists, delete
			# it first.
	ranlib libstuff.a	# puts in index
    # Example 2:
    gcc -Wall -o aprg1 aprg1.c

	# need a libstuff.h file
	gcc -I../include -L../lib -o wibble wibble.c -lstuff 
			# (means link against 'lib'stuff.a)
****
	# create a shared library
	cc -o libshared.so import.o getuid.o -shared
	# to link
	gcc main.o -o getuid -L. -lshared -lstdc++

	DUP:	gcc -idirafter /opt/local/include/python2.1 -c environ.c
			cc -o environ.so environ.o -shared
****
	ldd getuid
		# show libraries containing it.
****
	gcc -static (vs -shared?) # guides gcc to choosing which lib, if both exist.
****
	# Gay book on Unix Prging - static library listing of commands.
	ar -r libpasswd.a import.o getuid.o
	ar -r ... (the same) # -r form preferred, today. (the same, just diff. syntax)
	ar -r libpasswd.a getuid.o 	# UPDATE getuid object module, in libpasswd library.

	ar -t libpasswd.a		# list contents
	ar -tv ...				# verbose listing (more detailed).
****

nm -Ap ./libresolv.so | egrep 'inet_aton|res_query|dn_expand'
	command to list symbols from object files.

99) split --b=1m big.tarZ 	# Linux
	find . -print | grep -i '\.pdf' | wc -l   # case-less way to find any files.
	cat x* >rebuild.file # return file, as so.

	(FREE BSD) split -b 20m big.tarZ
	split -b 70m -a 4 reallyBig.tarZ # Linux: --suffix-length=4

100) tar tvz afile.tarZ # just list file contents.

	echo These people are on: \( `w | egrep -v '(users|USER)' | cut --b=0-8 | paste - - - ` \), your system.
	# an advanced script, showing usage of back-quote evaluation and echo WHO is on system.

	Inside vim; "! ispell -t %"
    # Added .vimrc setting, just hit "Caps V."

Advanced grepping.
	grep -i print cox04c.py | egrep -v '\..$'
		grep usually replaces egrep. It is just "for more" complicated expressions, egrep is necessary.

101) ls -xa | less # shows wide listing.
	make troubling.project 2>&1 show_type.txt # capture both stdout and stderr.

102) using su.
	su root -c 'grep commands ...' # to not be root for everything.

103) root, making a detailed file listing (before zapping, them).
		1) A plain find command.
		2) A -type f find command.
		2b) Search all cat-files, for ".

		2c) vi, :%s/^/"/g and :%s/$/"/g . And change the $ to \$.
		2d) Also, spaces; need to be escaped - even inside a pair of quotes. :%s/ /\\ /gc.
	Nevermind, 2c and 2d...

		3) use cat | xargs to; ls -l

104) How to pull out?
	plain files: find -type f
	executables: -perm +100 (or +111) [Note: sometimes exe's marked files are such files. Stuff from outside myself.]
	dirs only: one level, ls -l | grep ^dr
	dirs all: find . -print >junk20.file; cat junk20.file | xargs ls -l /dev/null >junk21.file; grep ^dr junk21.file
		PBM: Only shows dir names, raw and flat, no /home/here/that/this/that formed.
	dirs all: -type d.	

105) Normal. co -l afile.txt; ci afile.txt
	rlog afile.txt # to see history revision list. Or view RCS file directly.
	co -u -r1.2 afile.txt # For grabbing old revisions, IMPORTANT use "unlock" option.

	# To effect "user owning" problems.
	ci -wroot afile.txt
	co -l -wroot afile.txt
	# Otherwise, manully edit the ./RCS file.

	# Plus, "set user=root" or "export user=glenrt4" for environment var., manually.

106) DIRECTORY LOGIC:
	Read very carefully, this is extremely arcane and sadistic Unix Lore.

	a) How 'exactly' do the permission bits on a DIR effect, reading, writing and viewing files; within it?
	b) tar cvf works great; with non-hidden files (the NON .thing guys). Once, you need to consider the hidden files. It gets very complicated. Even find, can fail on finding .hidden files.
	c) DO NOT do 'tar ... '.*'' # SINCE it explodes, the archiving. (I believe when it finds any links. It follows them into any dir.s! [UPWARDS], same and very dangerous with "rm" !!! )
	
Point 1: find . -name '.*' -print # works great. Only one secret. It DOES NOT traverse into a .hidden_DIR!

Point 2: If an owned dir, is marked non-write by user and other perms. It is a read-only dir; which even for the user. You CANNOT write a file, OR DELETE the files within that DIR. Due to the -w setting.

Point 3: Setting of +x and -x, for non-owners (be it by group or World-permissions); has the effect of toggling "possible reading," and nothing to do with listing.
	So, if a dir is +x to you, but all others are -SET. If you know the name of a file or DIR; you can VIEW it. (In the case of a sub-DIR, you can actually list it.)

Point 4: If you stupidly +rwx, your dir to everyone. Then, they can write in it. Which if they are smart, they could put a file; inside your ~root-dir's. Which is set such that YOU cannot delete it (-w!). And really aggravate the owner.	
	
Point 5: What if you +w only a dir? I don't know. Haven't seen it yet. I'll probably play with it on pythagoras, sometime. I'd presume, you couldn't list it (being an outside user, [the circle]). However, you'd have full permission to create a file.

Point 6: With xargs rm /dev/null. You can delete your /dev/null bit bucket. No fun.

Point 7: It is easy to create looped (circular) directory references.
	tar cvf whatever.tar * # Does not go into them. Scp does.

107) set noclobber
	( cc simple.c >compile.out) >&compile.err # does something special.
	# avoid unintentional over-writting.
	2>&1 is called "duplicating file descriptors."


