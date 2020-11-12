要熟练STL、string、数组，BOOST的用法

---

```c++
#include<algorithm>
//replace函数
string str;
std::replace (str.begin(), str.end(),",",' ');
//从string中删除所有某个特定字符.remove不会改变字符串长度，因此需要用erase删除末几位
str.erase(std::remove(str.begin(), str.end(), '\"'), str.end());
```



```C++
//split 函数
vector<string> split(string src, string splitCharactor)  
{  
    vector<string> coll;  
    int begin = 0, end = 0;   
    while (begin < src.length())  
    {  
        end = src.find(splitCharactor.c_str(), begin);  
        if (end == -1)  
            end = src.length();  
        coll.push_back(src.substr(begin, end - begin));  
        begin = end + splitCharactor.length();  
    }  
    return coll;  
} 
```



```C++
//string2char* 函数
char* string2char(string str,int size)
{
	char *char_out=new char[size];
	int i;
	for(i=0;i<str.length();i++)
	{
		char_out[i]=str[i];
	}
	char_out[i]='\0';
	return char_out;
}
```



- 指针，对某一地址数据修改的钥匙
- &引用，在C++中可以替代指针的作用，更加方便



```C++
//将b中内容的COPY复制到a中
char *strcpy(char* dest, const char *src);  
//复制n个字节
char  *strncpy(char *s2, const char *s1, size_t n);  
//从源src所指的内存地址的起始位置开始拷贝n个字节到目标dest所指的内存地址的起始位置中
void *memcpy(void *dest, const void *src, size_t n); 
内存地址可按字节加，表示自己偏移
```



> CppSqlite3_2使用：sqlite3.dll和sqlite3.h添加到工程目录下，将CppSQLite3.h 和CppSQLite3.cpp添加到工程中,在工程中添加lib。	
> A、添加工程的头文件目录：工程---属性---配置属性---c/c++---常规---附加包含目录：加上头文件存放目录。
> B、添加文件引用的lib静态库路径：工程---属性---配置属性---链接器---常规---附加库目录：加上lib文件存放目录。
> C 、然后添加工程引用的lib文件名：工程---属性---配置属性---链接器---输入---附加依赖项：加上lib文件名。



```C++
//SQlite数据库的使用
CppSQLite3DB db;  
db.open("data.db"); 
CppSQLite3Buffer sql;
sql.format("insert into Node(x,y)values(%f,%f)",x,y);
db.execDML(sql);
db.close();
//查询query及blob操作见代码MIF2NDS
```



- **char[]  如果不以‘\0’结尾会报错，所以需预留足够空间**

```C++
string --> int:
	string str;int i=atoi(str.c_str());
string -->float:
	string str;float f=atof(str.c_str());
```



```C++
vector<struct> name;
name.push_back(one_struct);/name.emplace_back(one_struct);
```



```C++
//计时
#include<ctime>
clock_t start,end;
start=clock();	
end=clock();
float time=(double)(end-start)/CLOCKS_PER_SEC;
```



```C++
//IO
#include <fstream>
ifstream file;
file.open(" ");
string str;
getline(file,str);
flie.close();
```



> // haiwei/calender_tool  //结构体数据初始化方法

> plug-in/Eigen3   Dense矩阵运算 
> 附加包含目录那里填上你放Eigen文件夹的位置即可



```
//ANSI和Unicode字符串转换算法
#include <wchar.h>
wchar_t* ANSItoUnicode(char *szProgID)//无法传递，应修改为传入字符串指针
{
	WCHAR szWideProgID[128]; 
	long lLen = MultiByteToWideChar(CP_ACP,0,szProgID,strlen(szProgID),szWideProgID,sizeof(szWideProgID)); 
	szWideProgID[lLen] = '\0'; 
	return szWideProgID;
}

void UnicodetoANSI(LPCWCH wszSomeString)
{
	char szANSIString [MAX_PATH]; 
	WideCharToMultiByte ( CP_ACP, WC_COMPOSITECHECK, wszSomeString, -1,szANSIString, sizeof(szANSIString), NULL, NULL ); 
}
```



```c++
//CHAR与TCHAR
CA2T();  //CHAR转TCHAR
CT2A();  //
CW2A();  //宽字节转单字节

MultiByteToWideChar和WideCharToMultiByte

ATL转换宏
#include<atlconv.h>  //ATL下
USES_CONVERSION; 
//ATL 7.0不需要USES_CONVERSION定义

wcout.imbue(locale("chs")); //表示输出时,使用的区域语言对象
```



```c++
//fopen
//FILE * fopen(const char * path, const char * mode);
"r" 以只读方式打开文件，该文件必须存在。
"w" 打开只写文件，若文件存在则文件长度清为0，即该文件内容会消失。若文件不存在则建立该文件。
"w+" 打开可读写文件，若文件存在则文件长度清为零，即该文件内容会消失。若文件不存在则建立该文件。
"a" 以附加的方式打开只写文件。若文件不存在，则会建立该文件，如果文件存在，写入的数据会被加到文件尾，即文件原先的内容会被保留。（EOF符保留）
"a+" 以附加方式打开可读写的文件。若文件不存在，则会建立该文件，如果文件存在，写入的数据会被加到文件尾后，即文件原先的内容会被保留。（原来的EOF符不保留）
"wb" 只写打开或新建一个二进制文件，只允许写数据。
"wb+" 读写打开或建立一个二进制文件，允许读和写。
"ab" 追加打开一个二进制文件，并在文件末尾写数据。
"ab+"读写打开一个二进制文件，允许读，或在文件末追加数据。

//fwrite(const void* buffer, size_t size, size_t count, FILE* stream);
//fread(void *buffer, size_t size, size_t count, FILE *stream);
    -- buffer:指向数据块的指针
    -- size:每个数据的大小，单位为Byte(例如：sizeof(int)就是4)
    -- count:数据个数
    -- stream:文件指针
例：    
char*FilePath="C:\\Users\\HCHO\\Desktop\\write.db";
fp=fopen(FilePath,"rb");
fread(&ia,4,1,fp);
fclose(fp);

fseek(fp, 0, SEEK_END);  //重定位流(数据流/文件)上的文件内部位置指针
size = ftell(fp);  //得到文件位置指针当前位置相对于文件首的偏移字节数
rewind(fp);	//将文件内部的指针重新指向一个流的开头
```



```c++
//format函数
string format(const char *pszFmt, ...)
{
    std::string str;
    va_list args;
    va_start(args, pszFmt);
    {
        int nLength = _vscprintf(pszFmt, args);
        nLength += 1;  //上面返回的长度是包含\0，这里加上
        std::vector<char> vectorChars(nLength);
        _vsnprintf(vectorChars.data(), nLength, pszFmt, args);
        str.assign(vectorChars.data());
    }
    va_end(args);
    return str;
}
```



- 给字符串赋值应该用双引号，单个字符的话用单引号。
- 双引号代表字符串，会在后面加一个\0。
- strlen 是一个函数，它用来计算指定字符串 str 的长度，但不包括结束字符（即 null 字符） 
- 关键字 sizeof 是一个单目运算符,它的参数可以是数组、指针、类型、对象、函数等



##### Thread线程库

```
get_id	返回关联线程的唯一标识符
joinable	指定关联的线程是否可连接
join	阻塞，直到关联的线程完成
detach	分离 thread 对象关联的线程
swap	交换两个线程对象所代表的底层句柄
operator=	关联指定对象的线程与当前对象
```



##### int main( int argc, char* argv[] ) 中arg和argv参数的解析

    argc:argument counter
    argv:argument vector
    
    第一个参数，int型的argc，为整型，用来统计程序运行时发送给main函数的命令行参数的个数，在VS中默认值为1。 
    第二个参数，char*型的argv[]，为字符串数组，用来存放指向的字符串参数的指针数组，每一个元素指向一个参数。各成员含义如下： 
            argv[0]指向程序运行的全路径名 
            argv[1]指向在DOS命令行中执行程序名后的第一个字符串 
            argv[2]指向执行程序名后的第二个字符串 
            argv[3]指向执行程序名后的第三个字符串 
            argv[argc]为NULL 



**添加动态链接库**

①选择Release/Debug，x86/x64平台

②VC++  包含目录Include、库目录dll/lib文件。

③链接器-输入-附加依赖项lib文件。或者在源代码中加入指令#pragma comment(lib,"XX.lib")

④C/C++-预处理器-预处理器定义

- 独立运行.exe程序时须将.dll文件放到同一目录下

- 静态库lib:lib包含代码本身，在编译时直接将代码加入到程序当中。
- 动态库dll:lib包含了函数所在的dll和dll中函数位置的入口信息,代码由运行时加载在进程空间中的dll提供。



屏蔽warning

#pragma warning(disable:4996)



C++中数字计算全用double或全用int，避免因编译器问题导致计算错误或者精度损失这种无畏的错误。



##### 宏定义：

**#ifndef A_H**意思是"if not define a.h" 如果不存在a.h

接着的语句应该 **#define A_H** 就引入a.h

最后一句应该写 **#endif** 否则不需要引入

**#else**





**模板类 template < typename T >**

template是声明一个模板，typename是声明一个虚类型T，这个T可以代替int、double等基本数据类型