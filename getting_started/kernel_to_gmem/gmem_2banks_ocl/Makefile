#Repo containing utility and libs repository to use
COMMON_REPO := ../../../

# Make file Includes
include $(COMMON_REPO)/utility/boards.mk
include $(COMMON_REPO)/libs/xcl2/xcl2.mk
include $(COMMON_REPO)/libs/opencl/opencl.mk
include $(COMMON_REPO)/libs/bitmap/bitmap.mk

# Host files and setting
host_SRCS=./src/host.cpp $(xcl2_SRCS) $(bitmap_SRCS)
host_HDRS=$(xcl2_HDRS) $(bitmap_HDRS) 
host_CXXFLAGS= -I./src/ -std=c++0x -I./src/ $(xcl2_CXXFLAGS) $(opencl_CXXFLAGS) $(bitmap_CXXFLAGS)
host_LDFLAGS=$(opencl_LDFLAGS)

EXES=host

# Kernel
apply_watermark_SRCS=./src/apply_watermark.cl
apply_watermark_CLFLAGS= -I./src --max_memory_ports apply_watermark

XOS=apply_watermark

# xclbin
apply_watermark_XOS=apply_watermark
apply_watermark_LDCLFLAGS=--sp apply_watermark_1.m_axi_gmem0:bank0 --sp apply_watermark_1.m_axi_gmem1:bank1

XCLBINS=apply_watermark

EXTRA_CLEAN=./output.bmp

# check
check_EXE=host
check_XCLBINS=apply_watermark
check_ARGS=./data/input.bmp ./data/golden.bmp

CHECKS=check

include $(COMMON_REPO)/utility/rules.mk

