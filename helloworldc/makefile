#-------begin
#下面2条命令利用先生成静态库的方式再链接，最终也可以生成可执行文件
#ar -r libassist.a assist.o assist2.o
#gcc -o helloworldc main.o -L./ -lassist
#-------end

#-------begin
#下面2条命令先生成动态库，然后再与main.o链接，生成可执行文件。
#可执行文件运行时需要libassist.so库，如果没有，则不能运行。
#gcc -fpic -shared -o libassist.so assist.c assist2.c
#gcc -o helloworldc main.o -L./ -lassist
#-------end

#-------begin
#下面3条命令先生成.o文件，再生成动态库，然后再与main.o链接，生成可执行文件。
#可执行文件运行时需要libassist.so库，如果没有，则不能运行。
#gcc -c main.c -c assist.c -c assist2.c
#gcc -fpic -shared -o libassist.so assist.o assist2.o
#gcc -o test main.o -L./ -lassist
#-------end
.PHONY : clean
OBJFILES = main.o assist.o assist2.o

all : helloworldc clean

helloworldc : $(OBJFILES)
	cc -o $@ $?

main.o : main.c assist.h assist2.h
	cc -c main.c

assist.o : assist.c assist.txt
	cc -c assist.c

assist2.o : assist2.c assist2.h
	 cc -c assist2.c

clean :
	rm $(OBJFILES)

cleanall :
	rm helloworldc $(OBJFILES)
