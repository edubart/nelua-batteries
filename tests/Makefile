NELUA=nelua
NFLAGS=-L..
NELUARUN=$(NELUA) $(NFLAGS)

test: \
	algorithm_test \
	bigint_test \
	datetime_test \
	ffi_test \
	fs_test \
	inspector_test \
	json_test \
	signal_test

test-all: test test-test test-wrappers

test-tester: \
	nester_test \

test-wrappers: \
	backtrace_test \
	sqlite3_test

ffi_test:
	$(NELUARUN) --shared-lib ffi_module.nelua -o ffi_module
	$(NELUARUN) ffi_test.nelua

%_test:
	$(NELUARUN) $@.nelua
