+++
title = 'half-life with forward fd'
date = 2024-08-30T21:47:00+07:00
draft = false
math = true
tags = ['finite difference', 'half-life']
authors = ['viridi']
url = '2118'
+++
Forward finite difference formula to obtain consistent half-life<!--more-->

Half-life refers to time required for a given quantity to decrease from its initial value to half [^bashyal_2023]. This concept plays important role in understanding the decay or radioactive substances in nuclear physics and it is also used by scientists to measure age of ancient artifacts through carbon dating [^simon_2024]. In a first order reaction the half-life unrestrained by the concentration of the reactant, but the half-lives of reactions with other orders hang on the concentrations of the reactants at the same time [^turito_2022]. While solving the equation in discrete form, e.g. using Finite Difference (FD) method [^yew_2011], chosen time step $\Delta t$ will influence the quantity, which does not match the half-time. The indenpendence of half-life to time step is given here. 

A differential equation of decaying quantity $N$ is

$$\tag{1}
\frac{dN}{dt} = - \lambda N,
$$

where $\lambda$ stands for decay constant and $t$ for time. Using following Forward FD

$$\tag{2}
\frac{dN}{dt} \approx \frac{N(t + \Delta t) - N(t)}{\Delta t},
$$

Eqn (2) can be written as

$$
\frac{N(t + \Delta t) - N(t)}{\Delta t} = -\lambda N(t),
$$

that would be arranged further into

$$\tag{3}
N(t + \Delta t) = (1 - \lambda \Delta t) N(t),
$$

which is the iterable formula to find the quantity $N$ at any time $t$. Then relation between quantity $N$ at time $t$ and $t + \Delta t$ is given by

$$
\frac{N(t + \Delta t)}{N(t)} = (1 - \lambda \Delta t),
$$

which can be generalized as

$$
\frac{N(t + n \Delta t)}{N(t)} = (1 - \lambda \Delta t)^n.
$$

Suppose that $t = 0$ and $n\Delta t = T_\frac12$, the half-life, then

$$
\tfrac12 = (1 - \lambda \Delta t)^n.
$$

Further rearrangement of the terms will give

$$
\lambda = \frac{\sqrt[n]{2} - 1}{\Delta t \sqrt[n]{2}}.
$$

The [half-life and decay constant](../2128) relation

$$
T_\frac12 = \frac{\ln 2}{\lambda}
$$

will turn into

$$\tag{4}
T_\frac12 = \left( \frac{\sqrt[n]{2} \ln 2}{\sqrt[n]{2} - 1} \right) \Delta t.
$$

Eqn (4) is showing the dependence of half-time $T_\frac12$ to time step $\Delta t$.


[^bashyal_2023]: Jyoti Bashyal, "Half-life Formula: Derivation, Application, Examples", Science Info, 13 Jun 2023, url https://scienceinfo.com/half-life-formula-derivation/ [20240830].
[^simon_2024]: Yara Simón, "Half-Life Formula: Components and Applications", HowStuffWorks, 14 Feb 2024, url https://science.howstuffworks.com/half-life-formula.htm [20240830].
[^turito_2022]: Turito Team USA, "Half-Life : Definition, Formula, Derivation (Zero & First-Order)", Turito, 5 Sep 2022, url https://www.turito.com/blog/chemistry/half-life [20240830].
[^yew_2011]: Alice C. Yew, "Numerical differentiation: finite differences", Applied Mathematics, Brown University, 22 Apr 2011, url https://www.dam.brown.edu/people/alcyew/handouts/numdiff.pdf [20240830].
