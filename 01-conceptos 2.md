---
title: "MODELOS SEMI ESTRUCTURALES PARA EL CRÉDITO AL CONSUMO"
author: "[Luis Ortiz-Cevallos](https://ortiz-cevallos.github.io/MYSELF/)"
date: "2023-03-31"
site: bookdown::bookdown_site
output: bookdown::gitbook
code_download: true
code_folding: hide
documentclass: book
bibliography: [book.bib, packages.bib]
biblio-style: apalike
link-citations: yes
---





# INTRODUCCIÓN

## Proceso ARMA

Un proceso autoregresivo con media móvil (ARMA) es tipicamente continuo. Para disponer de un proceso ARMA es requerido un **proceso ruido blanco**

Un proceso ruido blanco es aquel que cumple con las sigueintes condiciones:

\begin{align}
E(\epsilon_{t})&=0\\
Var(\epsilon_{t})&=\sigma^{2}\\
Cov(\epsilon_{t}, \epsilon_{t+j})&=0\;\; \forall j
\end{align}

Dado ese proceso ruido blanco, un proceso ARMA(p,q) es:

\begin{align}
x_{t}&= a+p_{1}x_{t-1}+p_{2}x_{t-2}+\cdots+p_{p}x_{t-p}+\epsilon_{t}+\theta_{1}\epsilon_{t-1}+\cdots+\theta_{q}\epsilon_{t-q}\\
x_{t}&= a+\sum_{j=1}^{p}p_{j}x_{t-j}+\epsilon_{t}+\sum_{j=1}^{q}\theta_{j}\epsilon_{t-j}
\end{align}

*Operador de rezago* si definimo *L* tal que $L(x_{t})=x_{t-1}$, es posible definir un polinomio de rezagos como:

$a(L)=1L^{0}+a_{1}L^{1}+\cdots+a_{p}L^{p}$

De manera que un proceso ARMA(p, q) pueda ser escrito como:
\begin{equation}
a(L)x_{t}=b(L)\epsilon_{t}
\end{equation}

Lo estupendo de un proceso ARMA(p,q) es que **no son únicos**. Permiten invertir el componente AR del proceso como un MA y viceversa. Considere un ARMA(1,0):

\begin{align}
x_{t}&=px_{t-1}+\epsilon_{t}\\ 
(1-pL)x_{t}&=\epsilon_{t}\\
x_{t}&=\frac{1}{(1-pL)}\epsilon_{t}\\
x_{t}&=\frac{1}{(1-pL)}\epsilon_{t}\frac{1+pL+p^{2}L^{2}+p^{3}L^{3}\cdots}{1+pL+p^{2}L^{2}+p^{3}L^{3}\cdots}\\
x_{t}&=(1+pL+p^{2}L^{2}+p^{3}L^{3}\cdots)\epsilon_{t}=b(L)\epsilon_{t}\\
x_{t}&=\sum_{j=0}^{\infty}p^{j}\epsilon_{t-j}
\end{align}

De manera análoga podemos pasar de un proceso MA(1) a uno AR($\infty$):
\begin{align}
x_{t}&=\epsilon_{t}+\theta\epsilon_{t-1}\\ 
x_{t}&=(1+\theta L)\epsilon_{t}\\
\frac{1}{(1+\theta L)}x_{t}&=\epsilon_{t}\\
\frac{1}{(1+\theta L)}x_{t}\frac{1-\theta L-\theta^{2}L^{2}-\theta^{3}L^{3}\cdots}{1-\theta L-\theta^{2}L^{2}-\theta^{3}L^{3}\cdots}&=\epsilon_{t}\\
(1-\theta L-\theta^{2}L^{2}-\theta^{3}L^{3}\cdots)x_{t}&=a(L)x_{t}=\epsilon_{t}\\
\sum_{j=0}^{\infty}-\theta^{j}x_{t}&=\epsilon_{t-j}
\end{align}

Los anteriores resultados muestran que se puede estimar un proceso MA aproximándolo como un proceso AR. Un proceso AR puede ser estimado consistentemente a través de OLS.

