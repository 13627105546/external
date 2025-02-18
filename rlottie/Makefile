#
# Copyright (C) 2020 Xiaomi Corporation
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

include $(APPDIR)/Make.defs

CXXEXT := .cpp

CXXSRCS  += $(wildcard rlottie/src/binding/c/*.cpp)
CXXSRCS  += $(wildcard rlottie/src/lottie/*.cpp)
CXXSRCS  += $(wildcard rlottie/src/vector/*.cpp)
CXXSRCS  += $(wildcard rlottie/src/vector/freetype/*.cpp)
CXXSRCS  += $(wildcard rlottie/src/vector/stb/*.cpp)

CXXFLAGS += ${INCDIR_PREFIX}.
CXXFLAGS += ${INCDIR_PREFIX}rlottie/src/vector
CXXFLAGS += ${INCDIR_PREFIX}rlottie/src/vector/freetype

ifneq ($(CONFIG_ARM_NEON)$(CONFIG_ARM64_NEON),)
ASRCS += $(wildcard rlottie/src/vector/pixman/*.S)
endif

ifneq ($(CONFIG_LOTTIE_TEST),)
${shell mkdir -p $(BOARD_DIR)/resource/rlottie}
${shell cp rlottie/example/resource/mask.json $(BOARD_DIR)/resource/rlottie}
CXXFLAGS += -DDEMO_DIR=\"/resource/rlottie\"
# ignore warning: variable ‘r3’/‘r4’ set but not used
CXXFLAGS += -Wno-unused-but-set-variable
PRIORITY = $(CONFIG_LOTTIE_TEST_PRIORITY)
STACKSIZE = $(CONFIG_LOTTIE_TEST_STACKSIZE)
MODULE = $(CONFIG_LOTTIE_TEST)
MAINSRC = rlottie/test/testsuite.cpp
PROGNAME = gtest_rlottie
endif

include $(APPDIR)/Application.mk
