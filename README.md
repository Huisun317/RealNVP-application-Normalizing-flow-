# RealNVP-application-Normalizing-flow-
Some examples of applying realNVP to problems of interest

One of the major goal in stochastic computing is sampling, i.e. given a density $\nu(dx)$, how to efficiently sample random variables from such a distribution. Suppose that 
	$$\nu(dx) = \rho(x)dx$$ 
for some density $\rho(x)$. 

In this work, we propose a transportation method to do such sampling. That is, with the information that it's difficult to sample from the distribution $\nu(dx)$, we want to find a transport map $$T_*:\Omega \rightarrow \Omega$$ such that the following equation holds:
$$\int_{\Omega} O(T_{*}(x)) \rho_B(x)dx = \int_{\Omega} O(x) \rho_*(x)dx$$
We comment that the existence of the map $T_*$ is guaranteed by the optimal transportation theory.  To distinguish between the base space and the target domain, we use $\Omega_x$ and $\Omega_y$ to denote $\Omega$ even though these two are the same. 

We denote by $\bar{T}$ the inverse of the exact map $T_*$, then by a change of coordinate in 
\begin{align}{\label{}}
	\int_{\Omega_x} O(T_{*}(\bar{T}(y)))\rho_B(\bar{T}(y)) d\bar{T}(y) &= \int_{\Omega_y} O(y) \rho_B(\bar{T}(y)) \det|\nabla_y \bar{T}(y)| dy \\
	&= \int_{\Omega_y} O(y) \rho_*(y)dy 
\end{align}
As a result, we have the following relationship
\begin{align}
	\rho_B(\bar{T}(y)) \det|\nabla_y \bar{T}(y)| =\rho_*(y)
\end{align}
Now the question is how to construct such map $T$ that can approximate the true map $T_*$. W Now our goal is to construct an approximation of the transport map $T_*$. 
