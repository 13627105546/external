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

CSRCS += $(wildcard zint/backend/*.c)

CFLAGS += -DNO_PNG
CFLAGS += ${INCDIR_PREFIX}zint/backend

ifneq ($(CONFIG_UTILS_ZINT),)
  PRIORITY  = $(CONFIG_UTILS_ZINT_PRIORITY)
  STACKSIZE = $(CONFIG_UTILS_ZINT_STACKSIZE)
  PROGNAME  = $(CONFIG_UTILS_ZINT_PROGNAME)
  MODULE    = $(CONFIG_UTILS_ZINT)
  MAINSRC  += zint/frontend/main.c
endif

include $(APPDIR)/Application.mk
