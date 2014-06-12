# autoconf initialization (mandatory) including information about the project
AC_INIT([ACME TEST], 
        [1.0.0], 
        [jayesh@mcs.anl.gov], 
        [acme_test], 
        [])

# keep libtool macros in config directory.
AC_CONFIG_MACRO_DIR([config])

# specify config directory as the place where automake will look for various helper scripts
AC_CONFIG_AUX_DIR([config])

# check for autoconf API version >= 2.68
AC_PREREQ([2.68])

# automake initialization (mandatory) including a check for automake API version >= 1.11.1
AM_INIT_AUTOMAKE([1.11.1 tar-ustar])

# check for libtool API version >= 2.4
LT_PREREQ([2.4])

# use the C++ compiler for the following checks
AC_LANG([C++])

# libtool initialization, turn off shared library
#LT_INIT([disable-shared])
AM_DISABLE_SHARED
LT_INIT()

# copyright 
AC_COPYRIGHT(See COPYRIGHT in top-level directory)

# generate header files
#AC_CONFIG_HEADERS([src/include/hellow_conf.h])

# check for C++ preprocessor and compiler (might change the compiler flags)
AC_PROG_CXXCPP
AC_PROG_CXX
AC_PROG_INSTALL

################################################################################
# Debug Options
################################################################################

AC_MSG_CHECKING([whether to build with debug information])
AC_ARG_ENABLE([debug],
    [AS_HELP_STRING([--enable-debug],
        [enable debug data generation (def=no)])],
    [debugit="$enableval"],
    [debugit=no])
AC_MSG_RESULT([$debugit])

if test x"$debugit" = x"yes"; then
    AC_DEFINE([DEBUG],[],[Debug Mode])
    CXXFLAGS="$CXXFLAGS -g -O0"
    AM_SILENT_RULES(no)
else
    AC_DEFINE([NDEBUG],[],[No-debug Mode])
    CXXFLAGS="$CXXFLAGS -O2"
    AM_SILENT_RULES(yes)
fi

# files to generate via autotools
AC_CONFIG_FILES([Makefile 
                 src/Makefile
                 test/Makefile])

# generates the Makefiles etc. for the build
AC_OUTPUT
