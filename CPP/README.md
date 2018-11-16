# C++ Techniques
## #ifndef #define #endif
- 主要是编译器的识别
- 用于防止头文件被重复包含，提高编译器的编译效率
- 声明后的内容实验头文件名全大写，在中间使用下划线```_```隔开
```(C++)
#ifdef GRAPH_H      //如果不存在graph.h这个头文件（编译器链接到这个源文件中包含的```.h```文件时）
#define GRAPH_H     //就引入graph.h

//头文件的定义内容

#endif              //否则就不引入graph.h这个头文件
```

---
