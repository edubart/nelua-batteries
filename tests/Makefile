NELUA=nelua
NFLAGS=-L..
NELUARUN=$(NELUA) $(NFLAGS)

test: \
	test-fs \
	test-json \
	test-ffi \
	test-backtrace \
	test-nester \
	test-inspector

test-fs:
	$(NELUARUN) fs_test.nelua

test-json:
	$(NELUARUN) json_test.nelua

test-backtrace:
	$(NELUARUN) backtrace_test.nelua

test-ffi:
	$(NELUARUN) --shared-lib ffi_module.nelua -o ffi_module
	$(NELUARUN) ffi_test.nelua

test-nester:
	$(NELUARUN) nester_test.nelua

test-inspector:
	$(NELUARUN) inspector_test.nelua
