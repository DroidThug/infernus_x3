#_________________________________________________________________________#
# Makefile to make target device's installer zip                          #
# Copyright (C) 2017-2069 Sai Vishal (DroidThug)                          #
#                                                                         #
# This program is free software: you can redistribute it and/or modify    #
# it under the terms of the GNU General Public License as published by    #
# the Free Software Foundation, either version 3 of the License, or       #
# (at your option) any later version.                                     #
#                                                                         #
# This program is distributed in the hope that it will be useful,         #
# but WITHOUT ANY WARRANTY; without even the implied warranty of          #
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the           #
# GNU General Public License for more details.                            #
#                                                                         #
# You should have received a copy of the GNU General Public License       #
# along with this program.  If not, see <http://www.gnu.org/licenses/>.   #
#_________________________________________________________________________#

#----------#
# Usage:   # 
# make zip #
#----------#

#---------------------------------------------------------------------------

# //variables
# Modify these accordingly

# Kernel name
TARGET_KERNEL_NAME := INFERNUS

# Build date
KERNEL_BUILD_DATE := $(shell date +%s)

# Versioning
ifdef KERNEL_TAG_VERSION
KERNEL_TAG_VERSION := $(KERNEL_TAG_VERSION) 
else 
KERNEL_TAG_VERSION := UNOFFICIAL
endif

# Release directory
REL_DIR := infernus/release/

# Zip Structure directory
STRUCT_DIR := $(REL_DIR)/AnyKernel2/

# Output directory
OUT_DIR := infernus/out/

# Architecture of your device
ARCH := arm64

# Image name
IMAGE_NAME := Image.gz-dtb

# Image path
IMAGE_PATH := arch/$(ARCH)/boot/$(IMAGE_NAME)

# Final zip name
ZIP_TARGET_NAME := $(TARGET_KERNEL_NAME)-$(KERNEL_TAG_VERSION)_$(KERNEL_BUILD_DATE).zip

# Zip target files
ZIP_TARGETS := $(IMAGE_PATH)

# //script
.PHONY: zip infernus
infernus: zip
zip:
	@echo ------------ Making AnyKernel2/ ZIP installer ------------
	git submodule foreach git pull origin master
	rm -rf $(OUT_DIR)
	mkdir $(OUT_DIR)
	rm -rf $(STRUCT_DIR)/README.md
	cp -r $(STRUCT_DIR)/* $(OUT_DIR)/
	cp -r $(ZIP_TARGETS) $(OUT_DIR)/
	zip -r9 $(ZIP_TARGET_NAME) $(OUT_DIR)/*
	mv $(ZIP_TARGET_NAME) infernus/
	@echo ------------ Successfully made installer zip at : infernus/$(ZIP_TARGET_NAME) ------------
