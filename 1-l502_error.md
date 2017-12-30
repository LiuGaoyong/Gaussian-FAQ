# l502 error


---

- ####  How this error is showed in the output file?
```
>>>>>>>>>> Convergence criterion not met.
SCF Done:  E(RB3LYP) =  -4049.96612106     A.U. after  129 cycles
NFock=128  Conv=0.23D-04     -V/T= 2.0016
KE= 4.043428818037D+03 PE=-1.078527227163D+04 EE= 2.119393178062D+03
Convergence failure -- run terminated.
Error termination via Lnk1e in /usr/local/g09/l502.exe at Tue Feb 21 18:51:15 2017.
```

---

- ####  Why this error occur?
The output has showed: "Convergence criterion not met" and "Convergence failure".
This means the SCF calculation convergence failure.

---

- #### How to solve?

1.  ######  Use "scf=(maxcycle=n)" to setup the maximum of SCF cycle, and the default value of "n" is 128;   (Suggestion: let "n<=512", because more cycle is not helpful.)
 
1. ###### If the "a" donot work and the molecule is symmetrical, you can use "scf=dsymm" or "scf=symm";
 
1. ######  Use "scf=nosymm" or modified the molecule structure to break its symmetry;(Tip: the latter is more efficient than the former.)

1. ######  Use "qc" keyword, but it's very expensive. You can use "xqc", like "scf=(maxcycle=80,xqc)".
    ==Note: "scf=(maxcycle=80,xqc)" means the computer perform "qc" calculation 
         if it's no convergence after 80 cycles.==
1. ######  Use lower level model chemistry, for example, use small basic set to get convergence then use "gusee=read" to read the initial guess structure from that checkpoint file when you use big basic set.
	==Note==: it is very efficient in the case involved diffuse basic set such as 6-31+G*(6-31G*) or Aug-cc-pVTZ(cc-pVTZ)
	Warning: you'd better apply this way on small system.
1. ######  If they all do not work for your job, rebuilt it. Maybe the molecule you built is very terrible



---
---

中文版（来自 Google Translate）

- #### 输出文件告诉我们什么？
```
>>>>>>>>>> Convergence criterion not met.
SCF Done:  E(RB3LYP) =  -4049.96612106     A.U. after  129 cycles
NFock=128  Conv=0.23D-04     -V/T= 2.0016
KE= 4.043428818037D+03 PE=-1.078527227163D+04 EE= 2.119393178062D+03
Convergence failure -- run terminated.
Error termination via Lnk1e in /usr/local/g09/l502.exe at Tue Feb 21 18:51:15 2017.
```

---

- #### 为什么会发生这个错误？
结果显示：“不符合收敛标准”和“收敛失败”。
##### 这意味着==SCF计算收敛失败==。

---

- #### 怎么解决？

1. ######  一个。使用“scf =（maxcycle = n）”设置SCF周期的最大值，“n”的默认值为128; （建议：让“n <= 512”，因为更多的循环没有帮助。）
1. ######  如果“a”无效并且分子是对称的，则可以使用“scf = dsymm”或“scf = symm”;
1. ###### 使用“scf=nosymm”或修改分子结构来打破其对称性（提示：后者比前者更有效）。

1. ###### 使用“qc”关键字，但它非常昂贵。你可以使用“xqc”，比如“scf =（maxcycle = 80，xqc）”；注意：“scf =（maxcycle = 80，xqc）”表示计算机执行“qc”计算如果80个循环后没有收敛
1. ###### 使用低级模型化学，例如，使用小的基本集合来获得收敛；
    使用“gusee = read”来读取该检查点文件的初始猜测结构大的基本设置。
    注意：在涉及漫反射基本设置的情况下非常高效
    如6-31 + G *（6-31G *）或Aug-cc-pVTZ（cc-pVTZ）
    警告：你最好在小系统上应用这种方法。
1. ###### 如果他们都不适合你的工作，重建它。也许你建立的分子是非常可怕的