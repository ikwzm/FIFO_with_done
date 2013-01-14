
DUMMY_PLUG_PATH      = ../../Dummy_Plug
DUMMY_PLUG_WORK_PATH = $(DUMMY_PLUG_PATH)/sim/ghdl/dummy_plug
PIPEWORK_PATH        = ../../PipeWork
PIPEWORK_WORK_PATH   = ../../PipeWork/sim/ghdl/pipework

GHDL       = ghdl
GHDLFLAGS  = --mb-comments -P$(PIPEWORK_WORK_PATH) -P$(DUMMY_PLUG_WORK_PATH)

MAIN_SRC_PATH   = ../../src/main/vhdl
TEST_SRC_PATH   = ../../src/test/vhdl

TEST_BENCH = fifo_with_done_test_bench           \
             fifo_with_done_test_bench_async_5_9 \
             fifo_with_done_test_bench_async_9_5 \
             $(END_LIST)

all: $(TEST_BENCH)

clean:
	rm -f *.o *.cf $(TEST_BENCH)

$(TEST_BENCH) : $(addsuffix .o,$(TEST_BENCH))
	 $(GHDL) -e $(GHDLFLAGS) --work=WORK $@
	-$(GHDL) -r $(GHDLFLAGS) --work=WORK $@

DUT : fifo_with_done.o fifo_with_done_ctrl.o fifo_with_done_ctrl_sync.o fifo_with_done_components.o

fifo_with_done_components.o: $(TEST_SRC_PATH)/fifo_with_done_components.vhd
	 $(GHDL) -a $(GHDLFLAGS) --work=WORK $<

fifo_with_done_test_bench.o: $(TEST_SRC_PATH)/fifo_with_done_test_bench.vhd DUT
	 $(GHDL) -a $(GHDLFLAGS) --work=WORK $<

fifo_with_done_test_bench_async_5_9.o: $(TEST_SRC_PATH)/fifo_with_done_test_bench_async_5_9.vhd
	 $(GHDL) -a $(GHDLFLAGS) --work=WORK $<

fifo_with_done_test_bench_async_9_5.o: $(TEST_SRC_PATH)/fifo_with_done_test_bench_async_9_5.vhd
	 $(GHDL) -a $(GHDLFLAGS) --work=WORK $<

fifo_with_done.o           : $(MAIN_SRC_PATH)/fifo_with_done.vhd
	 $(GHDL) -a $(GHDLFLAGS) --work=WORK $<

fifo_with_done_ctrl.o      : $(MAIN_SRC_PATH)/fifo_with_done_ctrl.vhd
	 $(GHDL) -a $(GHDLFLAGS) --work=WORK $<

fifo_with_done_ctrl_sync.o : $(MAIN_SRC_PATH)/fifo_with_done_ctrl_sync.vhd
	 $(GHDL) -a $(GHDLFLAGS) --work=WORK $<
