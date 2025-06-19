ENTITY_FILES = ../../main/vhdl/fifo_with_done.vhd \
               ./fifo_with_done_test_bench.vhd

components.vhd : ${ENTITY_FILES}
	../../../PipeWork/tools/MakeComponentPackage.rb --verbose \
            --brief   'FIFO_WITH_DONE COMPONENT LIBRARY DESCRIPTION' \
            --version 0.2.0 \
            --author  'Ichiro Kawazome <ichiro_k@ca2.so-net.ne.jp>' \
            --library WORK \
            --package FIFO_WITH_DONE_COMPONENTS \
            --output  fifo_with_done_components.vhd \
            ${ENTITY_FILES}

clean:
	-rm fifo_with_done_components.vhd
