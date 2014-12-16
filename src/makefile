#-----------------------------------------------------------------------------
# File    : makefile
# Contents: build MEX-files
#           NB: tested with Matlab R2011b
# Author  : Kristian Loewe
#-----------------------------------------------------------------------------
.SUFFIXES:                                   # remove built-in rules
MAKEFLAGS  += -r

SHELL      = /bin/bash
CPUINFODIR = ../../cpuinfo/src

MATLABROOT = $(dir $(realpath $(shell which matlab)))
MEX        = $(realpath $(MATLABROOT))/mex
OPTS       = -O
# OPTS     = -v -O                           # verbose mex output
# OPTS     = -g -v -O                        # verbose mex output & debugging
DEFS       =
CFLAGS     = CFLAGS='-Wall -Wextra -Wno-unused-parameter -Wconversion \
             -pedantic -fPIC -std=c99 -march=native'
INCS       = -I$(CPUINFODIR)
SUF        = mexa64
OUTDIR     = ../private

PRGS       = $(addprefix $(OUTDIR)/, mxNProc.$(SUF) \
               mxHasMmx.$(SUF) mxHasSse.$(SUF) mxHasSse2.$(SUF) \
               mxHasSse3.$(SUF) mxHasSsse3.$(SUF) mxHasSse41.$(SUF) \
               mxHasSse42.$(SUF) mxHasPopcnt.$(SUF) mxHasAvx.$(SUF) )

#-----------------------------------------------------------------------------
# Build Programs
#-----------------------------------------------------------------------------
all: $(PRGS)

$(PRGS): | $(OUTDIR)

$(OUTDIR):
	mkdir -p $(OUTDIR)

# nproc
$(OUTDIR)/mxNProc.$(SUF): mxCpuinfo.c $(CPUINFODIR)/cpuinfo.* makefile
	$(MEX) $(OPTS) $(DEFS) -DFEATURE=nproc $(CFLAGS) \
  $(INCS) $< $(CPUINFODIR)/cpuinfo.c -outdir $(OUTDIR) -output $@

# mmx
$(OUTDIR)/mxHasMmx.$(SUF): mxCpuinfo.c $(CPUINFODIR)/cpuinfo.* makefile
	$(MEX) $(OPTS) $(DEFS) -DFEATURE=mmx $(CFLAGS) \
  $(INCS) $< $(CPUINFODIR)/cpuinfo.c -outdir $(OUTDIR) -output $@

# sse
$(OUTDIR)/mxHasSse.$(SUF): mxCpuinfo.c $(CPUINFODIR)/cpuinfo.* makefile
	$(MEX) $(OPTS) $(DEFS) -DFEATURE=sse $(CFLAGS) \
  $(INCS) $< $(CPUINFODIR)/cpuinfo.c -outdir $(OUTDIR) -output $@

# sse2
$(OUTDIR)/mxHasSse2.$(SUF): mxCpuinfo.c $(CPUINFODIR)/cpuinfo.* makefile
	$(MEX) $(OPTS) $(DEFS) -DFEATURE=sse2 $(CFLAGS) \
  $(INCS) $< $(CPUINFODIR)/cpuinfo.c -outdir $(OUTDIR) -output $@

# sse3
$(OUTDIR)/mxHasSse3.$(SUF): mxCpuinfo.c $(CPUINFODIR)/cpuinfo.* makefile
	$(MEX) $(OPTS) $(DEFS) -DFEATURE=sse3 $(CFLAGS) \
  $(INCS) $< $(CPUINFODIR)/cpuinfo.c -outdir $(OUTDIR) -output $@

# ssse3
$(OUTDIR)/mxHasSsse3.$(SUF): mxCpuinfo.c $(CPUINFODIR)/cpuinfo.* makefile
	$(MEX) $(OPTS) $(DEFS) -DFEATURE=ssse3 $(CFLAGS) \
  $(INCS) $< $(CPUINFODIR)/cpuinfo.c -outdir $(OUTDIR) -output $@

# sse4.1
$(OUTDIR)/mxHasSse41.$(SUF): mxCpuinfo.c $(CPUINFODIR)/cpuinfo.* makefile
	$(MEX) $(OPTS) $(DEFS) -DFEATURE=sse41 $(CFLAGS) \
  $(INCS) $< $(CPUINFODIR)/cpuinfo.c -outdir $(OUTDIR) -output $@

# sse4.2
$(OUTDIR)/mxHasSse42.$(SUF): mxCpuinfo.c $(CPUINFODIR)/cpuinfo.* makefile
	$(MEX) $(OPTS) $(DEFS) -DFEATURE=sse42 $(CFLAGS) \
  $(INCS) $< $(CPUINFODIR)/cpuinfo.c -outdir $(OUTDIR) -output $@

# popcnt
$(OUTDIR)/mxHasPopcnt.$(SUF): mxCpuinfo.c $(CPUINFODIR)/cpuinfo.* makefile
	$(MEX) $(OPTS) $(DEFS) -DFEATURE=popcnt $(CFLAGS) \
  $(INCS) $< $(CPUINFODIR)/cpuinfo.c -outdir $(OUTDIR) -output $@

# avx
$(OUTDIR)/mxHasAvx.$(SUF): mxCpuinfo.c $(CPUINFODIR)/cpuinfo.* makefile
	$(MEX) $(OPTS) $(DEFS) -DFEATURE=avx $(CFLAGS) \
  $(INCS) $< $(CPUINFODIR)/cpuinfo.c -outdir $(OUTDIR) -output $@