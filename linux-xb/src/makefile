# 
# ������Ϊ��ѡ���Դ������
# �������İ�Ȩ(����Դ�뼰�����Ʒ����汾)��һ�й������С�
# ����������ʹ�á�������������
# ��Ҳ�������κ���ʽ���κ�Ŀ��ʹ�ñ�����(����Դ�뼰�����Ʒ����汾)���������κΰ�Ȩ���ơ�
# =====================
# ����: ������
# ����: sunmingbao@126.com
# 

SRC_PATH=$(shell pwd)
OBJ_PATH=$(LIB_OBJ_PATH)
DEP_PATH=$(LIB_DEP_PATH)
SRC_FILES=$(wildcard $(SRC_PATH)/*.c)
SRC_FILES_BASE_NAMES=$(basename $(notdir $(SRC_FILES)))
OBJ_FILES=$(addprefix $(OBJ_PATH)/, $(addsuffix .o, $(SRC_FILES_BASE_NAMES)))
SOBJ_FILES=$(addprefix $(OBJ_PATH)/, $(addsuffix .sobj, $(SRC_FILES_BASE_NAMES)))
DEP_FILES=$(addprefix $(DEP_PATH)/, $(addsuffix .d, $(SRC_FILES_BASE_NAMES)))

all: $(LIB_FILE_STATIC)

.PHONY:all

$(LIB_FILE_STATIC): $(OBJ_FILES)
	@echo -n Building $@ ...
	@$(AR) -rcs $@ $^
	@echo done!


$(OBJ_PATH)/%.o: $(SRC_PATH)/%.c $(DEP_PATH)/%.d
	@echo -n Building $@ ...
	@$(CC) $(CFLAGS) $(INC_DIRS) $< -o $@ 
	@echo done!

$(DEP_PATH)/%.d: $(SRC_PATH)/%.c
	@echo -n Building $@ ...
	@$(CC) -MM  $(CFLAGS) $(INC_DIRS) $< | \
        sed "s|$*\.o[ :]*|$(DEP_PATH)/$*.d : |g"> $@
	@echo done!


-include $(DEP_FILES)
