OBJ_DIR = ../../../obj/
BIN_DIR = ../../../bin/
UTILITIES_DIR = ../../utils/
# -------------------
# define our includes
# -------------------
INCLUDES = -I$(UTILITIES_DIR)/fileType/ \
			-I$(UTILITIES_DIR)/FileRecordTools/FileReaders/ \
           -I$(UTILITIES_DIR)/FileRecordTools/Records/ \
           -I$(UTILITIES_DIR)/GenomeFile/ \
           -I$(UTILITIES_DIR)/general/ \
 			-I$(UTILITIES_DIR)/BamTools/include \
			-I$(UTILITIES_DIR)/BamTools/src/ \
           -I$(UTILITIES_DIR)/version/
			

SUBDIRS = ./FileReaders \
		  ./Records \

	
# ----------------------------------
# define our source and object files
# ----------------------------------
SOURCES= FileRecordMgr.cpp FileRecordMgr.h
OBJECTS= FileRecordMgr.o RecordOutputMgr.o
_EXT_OBJECTS=SingleLineDelimTextFileReader.o BamFileReader.o Bed3Interval.o Bed6Interval.o BedPlusInterval.o Bed12Interval.o BamRecord.o \
	SingleLineDelimTransferBuffer.o FileRecordTypeChecker.o QuickString.o ParseTools.o RecordKeyList.o BufferedStreamMgr.o
EXT_OBJECTS=$(patsubst %,$(OBJ_DIR)/%,$(_EXT_OBJECTS))
BUILT_OBJECTS= $(patsubst %,$(OBJ_DIR)/%,$(OBJECTS))

$(BUILT_OBJECTS): $(SOURCES) $(SUBDIRS)
	@echo "  * compiling FileRecordMgr.cpp"
	@$(CXX) -c -o $(OBJ_DIR)/FileRecordMgr.o FileRecordMgr.cpp $(LDFLAGS) $(CXXFLAGS) $(INCLUDES)
	
	

.PHONY: $(SUBDIRS)
$(SUBDIRS): $(OBJ_DIR)
	@echo "- Building in $@"
	@$(MAKE) --no-print-directory --directory=$@
	
clean:
	@echo "Cleaning up."
	@rm -f $(OBJ_DIR)/FileRecordMgr.o
	@rm -f $(OBJ_DIR)/RecordMgr.o
	@rm -f $(OBJ_DIR)/FileRecordTypeChecker.o
	@rm -f $(OBJ_DIR)/SingleLineDelimTextFileReader.o
	@rm -f $(OBJ_DIR)/SingleLineDelimTransferBuffer.o
	

.PHONY: clean