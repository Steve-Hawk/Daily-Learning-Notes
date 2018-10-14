# Fortan Learning Notes
-----------------------
**This is the documentation for learning fortran**

-----------------------
> ## Reference & Tutorial  
> [Online Tutorial](http://micro.ustc.edu.cn/Fortran/ZJDing)

### **Fortran annotation syntax**
* 'C' & '*' & '!' as the first character of the annotation
  
### Notes-1
* READ(* , *) a,b the first * means to the default output position(screen),the second * meands to read from the data using the default data format
* WRITE(* , *) the same as READ 

**Fortran Code - 1**
```fortran
! To calculate the average of a and b ! This is the annotation
      PROGRAM Example_1_1 ! This is the name of the fortran program
      REAL a, b, av1, av2 
      READ (*,*) a, b
      av1 = (a + b)/2
      av2 = sqrt(a*b)
      WRITE(*,*) av1, av2
      END
```
-------------------------------------------
*Tips: REAL::a,b approximately as REAL a,b but the former can assign value to variable a b directly*

-------------------------------------------
