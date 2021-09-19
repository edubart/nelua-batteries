NELUA=nelua
CC=gcc
NFLAGS=--cc=$(CC) -L..
NELUARUN=$(NELUA) $(NFLAGS)

test: \
	test-backtrace \
	test-ffi \
	test-fs

test-backtrace:
	$(NELUARUN) backtrace_test.nelua

test-ffi:
	$(NELUARUN) --shared-lib ffi_module.nelua -o ffi_module
	$(NELUARUN) ffi_test.nelua

test-fs:
	$(NELUARUN) fs_test.nelua
