# .PHONY: vcs sim clean

# TEST_DESIGN = adder_8bit

# vcs:
# 		vcs -sverilog +v2k -timescale=1ns/1ns       \
# 		-debug_all         							\
# 		-l compile.log 								\
# 		${TEST_DESIGN}.v testbench.v

# sim:
# 		./simv -l run.log

# clean:
# 		rm -rf *.log  csrc  simv*  *.key *.vpd  DVEfiles coverage *.vdb output.txt

.PHONY: compile sim clean

TEST_DESIGN = adder_8bit

compile:
	iverilog -g2012 -Wall -o simv $(TEST_DESIGN).v testbench.v

sim: compile
	vvp simv > run.log

clean:
	del /Q simv.* run.log *.vcd 2>nul || true