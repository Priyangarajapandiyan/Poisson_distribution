# Fitting Poisson  distribution
# Aim : 

To fit poisson distribution for the arrival of objects per minute from the feeder

# Software required :  

Python and Visual component tool

# Theory:

The Poisson distribution is the discrete probability distribution of the number of events occurring in a given time period, given the average number of times the event occurs over that time period.

![image](https://github.com/user-attachments/assets/e7ac9b7e-3f56-4600-9859-15e943032474)


 Conditions for Poisson Distribution:

1. An event can occur any number of times during a time period.
2. Events occur independently. I
3. The rate of occurrence is constant.
4. The probability of an event occurring is proportional to the length of the time period. 
 
# Procedure :
![image](https://github.com/user-attachments/assets/c5e61651-7315-4c17-91be-6df3e351546f)



# Experiment :
![image](https://github.com/user-attachments/assets/2dbb880f-00d0-4c32-bfc6-43f5e93e037f)


# Program :
```
import numpy as np
import math
import scipy.stats
L=[int(i) for i in input().split()]
N=len(L); M=max(L) 
X=list();f=list()
for i in range (M+1):
   c = 0
   for j in range(N):
       if L[j]==i:
           c=c+1
   f.append(c)
   X.append(i)
sf=np.sum(f)
p=list()
for i in range(M+1):
   p.append(f[i]/sf) 
mean=np.inner(X,p)
p=list();E=list();xi=list()
print("X P(X=x) Obs.Fr Exp.Fr xi")
print("--------------------------")
for x in range(M+1):
   p.append(math.exp(-mean)*mean**x/math.factorial(x))
   E.append(p[x]*sf)
   xi.append((f[x]-E[x])**2/E[x])
   print("%2.2f %2.3f %4.2f %3.2f %3.2f"%(x,p[x],f[x],E[x],xi[x]))
print("--------------------------")
cal_chi2_sq=np.sum(xi)
print("Calculated value of Chi square is %4.2f"%cal_chi2_sq)
table_chi2=scipy.stats.chi2.ppf(1-.01,df=M)
print("Table value of chi square at 1 level is %4.2f"%table_chi2)
if cal_chi2_sq<table_chi2:
   print("The given data can be fitted in poisson Distribution at 1% LOS")
else:
   print("The given data cannot be fitted in Poisson Distribution at 1% LOS")
```

# Output : 
![image](https://github.com/user-attachments/assets/ceb41146-3e0f-485e-8de3-9de63bcf9269)



# Results

The Poisson distribution is fitted for the objects arrived from feeder per minute and the data is tested using Chi-square test. 
 
