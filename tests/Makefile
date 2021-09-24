NELUA=nelua
CC=gcc
NFLAGS=--cc=$(CC) -L..
NELUARUN=$(NELUA) $(NFLAGS)

test: \
	test-fs \
	test-ffi \
	test-backtrace \
	test-nester

test-backtrace:
	$(NELUARUN) backtrace_test.nelua

test-ffi:
	$(NELUARUN) --shared-lib ffi_module.nelua -o ffi_module
	$(NELUARUN) ffi_test.nelua

test-fs:
	$(NELUARUN) fs_test.nelua

test-nester:
	$(NELUARUN) nester_test.nelua
