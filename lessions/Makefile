.PHONY : clean

LESSION=lession

# make 执行过程中所产生错误并不都是致命的；特别是在命令行之前存在'-'、或者make使用'-k'选项执行时。make执行过程的致命错误都带有前缀字符串'*'

STAGING_DIR=build
SUBDIRS := 00-helloworld 01-multilingual
SRCS:= $(foreach dir,$(SUBDIRS),$(wildcard $(dir)/*.tex))
OBJS:=$(patsubst %.tex, %.pdf, $(SRCS))
filenames := $(notdir $(filepaths))

#vpath %.tex ./00-helloworld ./01-multilingual

default: release

check:
	@echo $(SRCS)
	@echo $(OBJS)
	@echo "$$^=$^" 

$(OBJS): %.pdf:%.tex
	@echo "obj: $@, src: $<"
	xelatex -output-directory $(dir $<) $<

release: $(OBJS)

clean:
	@for dir in $(SUBDIRS); do \
           rm -rf $$dir/*.aux; \
           rm -rf $$dir/*.log; \
           rm -rf $$dir/*.pdf; \
         done
