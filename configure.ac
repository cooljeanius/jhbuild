dnl# configure.ac                                  -*- Autoconf -*-
dnl# Process this file with autoconf to produce a configure script.

AC_INIT([jhbuild],[2.32.4],
        [http://bugzilla.gnome.org/enter_bug.cgi?product=jhbuild])
AC_CONFIG_SRCDIR([jhbuild/main.py])
AC_CONFIG_AUX_DIR([build-aux])
AC_CONFIG_MACRO_DIR([build-aux])
AM_INIT_AUTOMAKE([-Wno-portability])
GNOME_COMMON_INIT
AM_MAINTAINER_MODE
AC_PREFIX_DEFAULT([~/.local/])dnl

AM_PATH_PYTHON

# i18n
GETTEXT_PACKAGE="jhbuild"
AC_SUBST([GETTEXT_PACKAGE])
AC_DEFINE_UNQUOTED([GETTEXT_PACKAGE],["${GETTEXT_PACKAGE}"],[Gettext package])
AM_GLIB_GNU_GETTEXT
IT_PROG_INTLTOOL([0.35.0])dnl

# Checks for programs.
AC_PROG_CC
PKG_PROG_PKG_CONFIG

# Checks for typedefs.
AC_TYPE_PID_T

# Checks for library functions.
AC_FUNC_FORK
AC_FUNC_MALLOC
AC_CHECK_FUNCS([strrchr])dnl

# Documentation:
AC_ARG_ENABLE([doc_installation],
	[AS_HELP_STRING([--enable-doc-installation=@<:@no/yes@:>@],
                        [install the documentation files])],
	[enable_doc_installation=${enableval}],
	[enable_doc_installation=no])
AM_CONDITIONAL([DOC_INSTALLATION_ENABLED],
               [test "x${enable_doc_installation}" = "xyes"])
# pkg-config check below is conditionalized since documentation is optional
AS_IF([test "x${enable_doc_installation}" = "xyes"],
      [PKG_CHECK_MODULES([GNOME_DOC_UTILS],[gnome-doc-utils])])
GNOME_DOC_INIT

# Output.
AC_CONFIG_FILES([
	Makefile
	doc/Makefile
	po/Makefile.in
	scripts/Makefile
	jhbuild/Makefile
	jhbuild/buildbot/Makefile
	jhbuild/buildbot/status/web/Makefile
	jhbuild/buildbot/status/Makefile
	jhbuild/commands/Makefile
	jhbuild/cut_n_paste/Makefile
	jhbuild/frontends/Makefile
	jhbuild/modtypes/Makefile
	jhbuild/utils/Makefile
	jhbuild/versioncontrol/Makefile
	buildbot/Makefile
])
AC_CONFIG_FILES([
	jhbuild.desktop.in
])
AC_OUTPUT
