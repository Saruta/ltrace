# Copyright (C) 2015 Petr Machata, Red Hat Inc.
# Copyright (C) 1992 - 2001 Free Software Foundation, Inc.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 1, or (at your option)
# any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#

AUTOMAKE_OPTIONS = dejagnu

if USE_VALGRIND
valgrind_cmd="VALGRIND=valgrind -q --error-exitcode=1 --leak-check=full"
endif

if ! HAVE_LIBDW
skip_dwarf = --ignore dwarf.exp
endif

RUNTESTDEFAULTFLAGS = --srcdir $(srcdir) $(valgrind_cmd) $(skip_dwarf)

SUBDIRS = ltrace.main ltrace.minor ltrace.torture

EXTRA_DIST = \
	README \
	config/unix.exp \
	lib/compiler.c \
	lib/compiler.cc \
	lib/ltrace.exp \
	run-my-tests.sh

BUILT_SOURCES = env.exp

env.exp: Makefile
	rm -f env.exp
	echo set libelf_LD_LIBRARY_PATH '"$(libelf_LD_LIBRARY_PATH)"' >> $@
	echo set elfutils_LD_LIBRARY_PATH '"$(elfutils_LD_LIBRARY_PATH)"' >> $@
	echo set libunwind_LD_LIBRARY_PATH '"$(libunwind_LD_LIBRARY_PATH)"' >> $@
	echo set PREFIX '"$(prefix)"' >> $@

CLEANFILES = *.o *.so *.log *.sum *.ltrace site.bak setval.tmp site.exp env.exp

MAINTAINERCLEANFILES = Makefile.in
