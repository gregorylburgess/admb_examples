#  Ordered categorical responses

Filed under:  [Categorical Data][4], [Social science][1]

The SOCATT data set is used in the comparison of different software packages for multilevel modelling, conducted by the [Centre for Multilevel Modelling][2]. The SOCATT data consist of the responses to a set of dichotomous items on a woman's right to have an abortion. The outcome variable (_y<sub>ij</sub>_) is a score constructed from these items ranging from 1 to 7, with a higher score corresponding to stronger support for abortion. Each of 264 respondents was asked the same set of questions on four occasions, 1983-1986, and _y<sub>ij</sub>_ denotes the response from individual _i_ in year _j_

. We consider one categorical covariate (religion) with 4 categories. A random intercept ordered logit model was fitted:

<img src="./logit.png" alt="Xt = σX exp(h2) εt" width="450" height="25">

<img src="./ui.png" alt="Xt = σX exp(h2) εt" width="125" height="25">

where _x1i_, _x2i_ and _x3i_ are dummy variables coding for the different levels of the categorical covariates, and _ks_ are threshold parameters. A full description of the model can be found here: [socatt.pdf][3]

 
 

[1]: https://github.com/admb-project/examples/search?utf8=%E2%9C%93&q=social+science
[2]: http://multilevel.ioe.ac.uk/softrev/index.html
[3]: ./socatt.pdf
[4]: ./../
