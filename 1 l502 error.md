l502 error

===============================================================================================
                  How this error is showed in the output file?
===============================================================================================
>>>>>>>>>> Convergence criterion not met.
SCF Done:  E(RB3LYP) =  -4049.96612106     A.U. after  129 cycles
NFock=128  Conv=0.23D-04     -V/T= 2.0016
KE= 4.043428818037D+03 PE=-1.078527227163D+04 EE= 2.119393178062D+03
Convergence failure -- run terminated.
Error termination via Lnk1e in /usr/local/g09/l502.exe at Tue Feb 21 18:51:15 2017.


===============================================================================================
                                Why this error occur?
===============================================================================================
The output has showed: "Convergence criterion not met" and "Convergence failure".
This means the SCF calculation convergence failure.

  
===============================================================================================
                                     How to solve?
===============================================================================================
a.Use "scf=(maxcycle=n)" to setup the maximum of SCF cycle, and the default value of "n" is 128;
    Suggestion: let "n<=512", because more cycle is not helpful.
b.If the "a" donot work and the molecule is symmetrical, you can use "scf=dsymm" or "scf=symm";
c.Use "scf=nosymm" or modified the molecule structure to break its symmetry;
    Tip: the latter is more efficient than the former.
d.Use "qc" keyword, but it's very expensive. You can use "xqc", like "scf=(maxcycle=80,xqc)".
    Note: "scf=(maxcycle=80,xqc)" means the computer perform "qc" calculation 
         if it's no convergence after 80 cycles.
e.Use lower level model chemistry, for example, use small basic set to get convergence then 
  use "gusee=read" to read the initial guess structure from that checkpoint file when you use 
  big basic set.
	Note: it is very efficient in the case involved diffuse basic set 
	     such as 6-31+G*(6-31G*) or Aug-cc-pVTZ(cc-pVTZ)
	Warning: you'd better apply this way on small system.
f.If they all do not work for your job, rebuilt it. Maybe the molecule you built is very terrible
===============================================================================================
