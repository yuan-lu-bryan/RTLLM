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

.PHONY: compile sim yosys visualize clean 

TEST_DESIGN = adder_8bit

OSS_CAD_SUITE_PATH = C:\Users\13862\oss-cad-suite

compile: 
	iverilog -g2012 -Wall -o simv $(TEST_DESIGN).v testbench.v

sim: compile
	vvp simv > run.log

yosys: sim
	@call $(OSS_CAD_SUITE_PATH)\environment.bat && yosys -p "read_verilog $(TEST_DESIGN).v; synth; write_json $(TEST_DESIGN).json"

visualize: yosys
	netlistsvg $(TEST_DESIGN).json -o $(TEST_DESIGN).svg

clean:
	del /Q simv.* run.log *.vcd *.json *.svg 2>nul || true