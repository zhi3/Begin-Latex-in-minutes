.PHONY : default release check clean

# make 执行过程中所产生错误并不都是致命的；特别是在命令行之前存在'-'、或者make使用'-k'选项执行时。make执行过程的致命错误都带有前缀字符串'*'

SUBDIRS := 00-helloworld 01-multilingual 02-lists 03-paragraph-section 04-tableofcontents \
           05-package 06-table 07-adding-images 08-insert-code
SRCS:= $(foreach dir,$(SUBDIRS),$(wildcard $(dir)/*.tex))
OBJS:=$(patsubst %.tex, %.pdf, $(SRCS))

#vpath %.tex ./00-helloworld ./01-multilingual

default: release

check:
	@echo $(SRCS)
	@echo $(OBJS)
	@echo "$$^=$^" 

$(OBJS): %.pdf:%.tex
	@echo "...... start obj: $@, src: $<"
	cd $(dir $<) && xelatex $(notdir $<)
	@echo "...... end"
#xelatex -output-directory $(dir $<) $<
release: $(OBJS)

clean:
	@for dir in $(SUBDIRS); do \
           rm -rf $$dir/*.aux; \
           rm -rf $$dir/*.log; \
           rm -rf $$dir/*.pdf; \
         done
