CXX = zig c++
CXXFLAGS = -Wall -g -MMD -MP

BUILD_DIR = build
SRC_DIR = src


SRCS = $(wildcard $(SRC_DIR)/*.cpp)

OBJS = $(SRCS:$(SRC_DIR)/%.cpp=$(BUILD_DIR)/%.o)

# This should make it work on both unix* systems and windows
ifeq ($(OS),Windows_NT)
        SHELL := cmd.exe
        .SHELLFLAGS := /c
        TARGET = main.exe
        PDBS = $(TARGET:.exe=.pdb)
        RUN = .\$(TARGET)
        MKDIR_FLAGS =
        RM = del /Q /F
        RRM = if exist build rmdir /Q /S
else
        TARGET = main
        PDBS =
        RUN = ./$(TARGET)
        MKDIR_FLAGS =-p
        RM = rm -f
        RRM = rm -f -r
endif

.PHONY: all run clean

all: $(TARGET) run

#Linking stage
$(TARGET) : $(OBJS)
        $(CXX) $(CXXFLAGS) -o $(TARGET) $(OBJS)

$(BUILD_DIR):
        mkdir $(MKDIR_FLAGS) $(BUILD_DIR)
#compiles all cpps to objects in a build dir
$(BUILD_DIR)/%.o: $(SRC_DIR)/%.cpp | $(BUILD_DIR)
        $(CXX) $(CXXFLAGS) -c $< -o $@

run: $(TARGET)
        $(RUN)

clean:
        $(RM) $(TARGET) $(PDBS)
        $(RRM) $(BUILD_DIR) 
