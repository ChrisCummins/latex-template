AC_PREREQ(2.65)

dnl
dnl                Autoconf script
dnl
dnl Copyright (c) 2013, 2014, 2015 Chris Cummins.
dnl
dnl Permission is hereby granted, free of charge, to any person
dnl obtaining a copy of this software and associated documentation
dnl files (the "Software"), to deal in the Software without
dnl restriction, including without limitation the rights to use, copy,
dnl modify, merge, publish, distribute, sublicense, and/or sell copies
dnl of the Software, and to permit persons to whom the Software is
dnl furnished to do so, subject to the following conditions:
dnl
dnl The above copyright notice and this permission notice shall be
dnl included in all copies or substantial portions of the Software.
dnl
dnl THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
dnl EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
dnl MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
dnl NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
dnl HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
dnl WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
dnl OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
dnl DEALINGS IN THE SOFTWARE.


dnl ================================================================
dnl The package version
dnl ================================================================
m4_define([author],[chrisc.101@gmail.com])
m4_define([major_version],[0])
m4_define([minor_version],[0])
m4_define([micro_version],[1])
m4_define([version],[major_version.minor_version.micro_version])


dnl ================================================================
dnl Project details (i.e. the "meta" stuff)
dnl ================================================================
AC_INIT([latex-template],[version],[author])
AC_CONFIG_AUX_DIR([build])

dnl Support for --program-prefix, --program-suffix and
dnl --program-transform-name options
AC_ARG_PROGRAM

dnl Fairly arbitrary, older versions might work too.
AM_INIT_AUTOMAKE([1.11 foreign -Wno-portability])
AM_SILENT_RULES([yes])


dnl ================================================================
dnl Dependencies
dnl ================================================================
AC_PROG_AWK
AC_PROG_EGREP
AC_PROG_SED


dnl ================================================================
dnl     Do we have pdflatex installed?
dnl ================================================================
AC_CHECK_PROG([PDFLATEX],[pdflatex],[pdflatex])
AS_IF([test "x$PDFLATEX" = x],
      [AC_MSG_ERROR([Required program \`pdflatex' not found.])])


dnl ================================================================
dnl Optional dependencies
dnl ================================================================


dnl ================================================================
dnl     Do we have bibtex installed?
dnl ================================================================
AC_CHECK_PROG([BIBTEX],[bibtex],[bibtex])
AS_IF([test "x$BIBTEX" != x],
      [HAVE_BIBTEX=yes],
      [HAVE_BIBTEX=no
       AC_MSG_WARN([No support for bibtex bibliography back-end.])])
AC_SUBST([HAVE_BIBTEX],[$HAVE_BIBTEX])
AM_CONDITIONAL([HAVE_BIBTEX],[test "x$HAVE_BIBTEX" = xyes])


dnl ================================================================
dnl     Do we have bibtool installed?
dnl ================================================================
AC_CHECK_PROG([BIBTOOL],[bibtool],[bibtool])
AS_IF([test "x$BIBTOOL" != x],
      [HAVE_BIBTOOL=yes],
      [HAVE_BIBTOOL=no
       AC_MSG_WARN([Unable to generate local bibliography files.])])
AC_SUBST([HAVE_BIBTOOL],[$HAVE_BIBTOOL])
AM_CONDITIONAL([HAVE_BIBTOOL],[test "x$HAVE_BIBTOOL" = xyes])


dnl ================================================================
dnl     Should xdg-open be used to open PDFs?
dnl ================================================================
AC_CHECK_PROG([PDF_VIEWER],[xdg-open],[xdg-open])
AS_IF([test "x$PDF_VIEWER" != x],
      [HAVE_PDF_VIEWER=yes],
      [HAVE_PDF_VIEWER=no
       AC_MSG_WARN([Unable to open PDF files.])])
AC_SUBST([HAVE_PDF_VIEWER],[$HAVE_PDF_VIEWER])
AM_CONDITIONAL([HAVE_PDF_VIEWER],[test "x$HAVE_PDF_VIEWER" = xyes])


dnl ================================================================
dnl     Should emacsclient be used for editing files?
dnl ================================================================
AC_CHECK_PROG([EDITOR],[emacsclient],[emacsclient])
AS_IF([test "x$EDITOR" != x],
      [HAVE_EDITOR=yes],
      [HAVE_EDITOR=no
       AC_MSG_WARN([Unable to launch text editor.])])
AC_SUBST([HAVE_EDITOR],[$HAVE_EDITOR])
AM_CONDITIONAL([HAVE_EDITOR],[test "x$HAVE_EDITOR" = xyes])


dnl ================================================================
dnl     Do we have texcount installed?
dnl ================================================================
AC_CHECK_PROG([TEXCOUNT],[texcount],[texcount])
AS_IF([test "x$TEXCOUNT" != x],
      [HAVE_TEXCOUNT=yes],
      [HAVE_TEXCOUNT=no
       AC_MSG_WARN([LaTeX word counts disabled.])])
AC_SUBST([HAVE_TEXCOUNT],[$HAVE_TEXCOUNT])
AM_CONDITIONAL([HAVE_TEXCOUNT],[test "x$HAVE_TEXCOUNT" = xyes])


dnl ================================================================
dnl     Do we have checkcites installed?
dnl ================================================================
AC_CHECK_PROG([CHECKCITES],[checkcites],[checkcites])
AS_IF([test "x$CHECKCITES" != x],
      [HAVE_CHECKCITES=yes],
      [HAVE_CHECKCITES=no
       AC_MSG_WARN([LaTeX citation checks disabled.])])
AC_SUBST([HAVE_CHECKCITES],[$HAVE_CHECKCITES])
AM_CONDITIONAL([HAVE_CHECKCITES],[test "x$HAVE_CHECKCITES" = xyes])


dnl ================================================================
dnl     Do we have textlint installed?
dnl ================================================================
AC_CHECK_PROG([TEXTLINT],[textlint],[textlint])
AS_IF([test "x$TEXTLINT" != x],
      [HAVE_TEXTLINT=yes],
      [HAVE_TEXTLINT=no
       AC_MSG_WARN([LaTeX style checks disabled.])])
AC_SUBST([HAVE_TEXTLINT],[$HAVE_TEXTLINT])
AM_CONDITIONAL([HAVE_TEXTLINT],[test "x$HAVE_TEXTLINT" = xyes])


dnl ================================================================
dnl Generate files
dnl ================================================================
AC_CONFIG_FILES([Makefile])

AC_OUTPUT

echo ""
echo "You can now run \`make'."
