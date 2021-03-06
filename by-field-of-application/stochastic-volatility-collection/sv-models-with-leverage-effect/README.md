#  SV models with leverage effect

Filed under: [Stochastic Volatility Collection][10]

 The leverage effect is the phenomenon that volatility tends to rise following a drop in returns. In SV models the leverage effect is modeled by letting the noise terms in the two equations be correlated. SV models with leverage effect can be written as:  
 
<img src="./../the-basic-sv-model-and-simple-extensions-1/eq1.png" alt="Xt = σX exp(h2) εt" width="125" height="25">

<img src="./../the-basic-sv-model-and-simple-extensions-1/eq2.png" alt="ht 1 = φht σηt" width="180" height="25">
  
 where the pairs (ε<sub>t</sub>, η<sub>t</sub>) are iid with E(ε<sub>t</sub>) = E(η<sub>t</sub>) = 0, Var(ε<sub>t</sub>) = Var(η<sub>t</sub>) = 1 and  corr(ε<sub>t</sub>, η<sub>t</sub>) = ρ.   
 
 If ρ < 0, which is the standard case, a drop in returns at time t then tends to give increased volatility at time t+1. 

 Due to correlated noise terms, the structure in SV models with leverage effect is (slightly) more complicated than in the models without leverage effect. It is therefore also more difficult to find an expression for the joint density function, p(<strong>X</strong>, <strong>h</strong>|θ), in this case.  SV models on the form (1-2) can be represented graphically as: 
 
 ![Fig_1][1]
 
All paths to  X<sub>t</sub> and h<sub>t+1</sub> goes via/through h<sub>t</sub>, so the pair (X<sub>t</sub>, h<sub>t+1</sub>) is conditionally independent of previous variables given h<sub>t</sub>. 
   
  This leads to the following expression for the joint density: 
  
 <img src="./probability1.png" alt="" width="380" height="25">
 
 This expression may be further simplified by factorizing  
 
 <img src="./probability2.png" alt="" width="130" height="20">.
 
 This can be done in two ways: 
 
 a. We can use that
 
 <img src="./probability3.png" alt="" width="600" height="25">
 
 and write the joint density as
 
 <img src="./probability4.png" alt="" width="600" height="25"> 
 
 This is represented in the folowing graph  
   ![Fig_2][2] 
  
  b. Alternatively we can use
  
  <img src="./probability5.png" alt="" width="600" height="25">, 
  
  which gives the following expression 
  
  <img src="./probability6.png" alt="" width="600" height="25">. 
  
  The graphical representation for this form is given by 
  
 ![Fig_3][3]
 
 The two forms should be equivalent, so it should in principle be possible to use both. However, as we shall see, it might be reasons to prefer one over the other.    
 
###<strong>The Gaussian leverage model</strong>
 In the Gaussian leverage model it is assumed that the pairs (ε<sub>t</sub>, η<sub>t</sub>) are iid bi-variate normally distributed, with standard normal marginals. This is the most popular leverage model and it is a discrete time version of models used in option pricing. 
 
 Then
 
 <img src="./g1.png" alt="LaTex equation" width="200" height="25">
 
 and we can write 
 
  <img src="./g2.png" alt="LaTex equation" width="150" height="25">
  
  where w<sub>t</sub> is standard normal and η<sub>t</sub> and w<sub>t</sub> are independent. Noting that 
  
  <img src="./g3.png" alt="LaTex equation" width="200" height="25">,
    
   the model can be written as: 
 
  <img src="./g4.png" alt="LaTex equation" width="600" height="25">, 
 
  <img src="./g5.png" alt="LaTex equation" width="200" height="25">, 
  
  where w<sub>t</sub> and η<sub>t</sub> are iid N(0,1).   
  
  On this form we may use the formulation a) for the joint density function, and we see that   
  
  <img src="./g6.png" alt="LaTex equation" width="250" height="45">, 
  
  and
  
  <img src="./g7.png" alt="LaTex equation" width="600" height="25">. 
 
 Thus it is easy to find an expression for log p(<strong>X</strong>, <strong>h</strong>|θ) here. See [sdv_lev_1.tpl][4] for how this can be done.   
 
 Alternatively we may use the other version. Noting that
 
 <img src="./g8.png" alt="LaTex equation" width="200" height="25">,
 
 we may write
 
 <img src="./g9.png" alt="LaTex equation" width="200" height="25">, 
 
 where 
 
<img src="./g10.png" alt="LaTex equation" width="100" height="25">

and v<sub>t</sub> is independent of ε<sub>t</sub>. Then, using that

<img src="./g11.png" alt="LaTex equation" width="300" height="25">,

the model may be written as: 
 
<img src="./g12.png" alt="LaTex equation" width="200" height="25">,
 
<img src="./g13.png" alt="LaTex equation" width="550" height="25">, 
 
 where ε<sub>t</sub> and v<sub>t</sub> are iid N(0,1) by assumption.  
 
 Here it is seen that 
 
 <img src="./g14.png" alt="LaTex equation" width="600" height="25">
 
 and
 
 <img src="./g15.png" alt="LaTex equation" width="350" height="20">),
 
 so we can easily find an expression for log p(<strong>X</strong>, <strong>h</strong>|θ), see [sdv_lev_2.tpl][5] for how this can be done.  
 
 The two specifications for the Gaussian leverage model should give the same results. Comparing the par files [sdv_lev_1.par][6] and [sdv_lev_2.par][4], we see that the results are practically identical, as they should. However, it seems that sdv_lev_1 runs somewhat faster and that the difference in run time is increasing in the size of the data set. This suggests that it might be preferable to use the parametrization given in sdv_lev_1, at least for large data sets. This version may be less intuitive than the other and is less commonly used, but it might actually be preferable because of the run time issue.   
 
###<strong>Leverage models with heavier tails and/or skewness</strong>
 
 The moments of returns in the Gaussian leverage model are the same as in the basic SV model. In order to model both leverage effect and heavier tails and/or skewness, the following specification is used: 
 
<img src="./g16.png" alt="LaTex equation" width="250" height="20">, 
 
<img src="./g17.png" alt="LaTex equation" width="450" height="25">, 
 
 where
 
 <img src="./g18.png" alt="LaTex equation" width="100" height="20"> and ε<sub>t</sub> has some standardized continuous distribution. This looks like the formulation used to set up sdv_lev2, but here ε<sub>t</sub> is not necessarily normally distributed. In the SV_lev_t model a standardized t-distribution is used for ε<sub>t</sub>. This not only gives heavier tails in the returns, but also some tail thickness in the volatility process. This might actually be a favorable property. In SV_lev_st  ε<sub>t </sub>follows a skewed t-distribution, which captures skewness in returns, but also gives skewness in the volatility process. If ε<sub>t </sub>has negative skewness and ρ also is negative, which is the usual case, then there is positive skewness in the volatility process. This seems like a reasonable property, since big positive “jumps” in volatility are more likely to occur than large negative ones.   
 
 For models on this form 
 
 <img src="./g19.png" alt="LaTex equation" width="700" height="25"> 
 
 no matter which distribution we choose for ε<sub>t</sub>. When ε<sub>t</sub>  is not normally distributed, the distribution of h<sub>1</sub>|θ is unknown, so strictly speaking we cannot find an exact expression for p(<strong>X</strong>,<strong>h</strong>|θ) here. However it is still the case that E[h<sub>1</sub>] = 0 and <img src="./g20.png" alt="LaTex equation" width="200" height="25">, and by assuming that <img src="./g21.png" alt="LaTex equation" width="200" height="25">, we find an approximate expression for the joint density. Since p(h<sub>1</sub>|θ) is only a minor contributor to p(<strong>X</strong>,<strong>h</strong>|θ), the error is small. The distribution of X<sub>t</sub>|h<sub>t</sub> depends on the distribution used for ε<sub>t</sub>, as can be seen in the tpl-files, [sdv_t_lev.tpl][8] and [sdv_st_lev][9]. 


[1]: Figure-2.jpeg "Fig_1"
[2]: Figure-3.jpeg "Fig_2"
[3]: Figure-4.jpeg "Fig_3"
[4]: sdv_lev_1.tpl "sdv_lev_1.tpl"
[5]: sdv_lev_2.tpl "sdv_lev_2.tpl"
[6]: sdv_lev_1.par "sdv_lev_1.par"
[7]: sdv_lev_2.par "sdv_lev_2.par"
[8]: sdv_t_lev.tpl "sdv_t_lev.tpl"
[9]: sdv_st_lev.tpl "sdv_st_lev.tpl"
[10]: ./../
