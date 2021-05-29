---
title: Probability Basics
date: 2019-1-31
tags: 
	- Probability
categories: 
	- Mathematics
	- Probability
	- Probability Theory
mathjax: true
---
This note contains basic knowledge of probability, including events, probability, conditional probability, multiplication theorem of probability, formula of total probability and Bayes' theorem.

# Probability Space

## Finite Sample Space

Generally, a set of all the possible results of a certain experiment $S$ is call the *sample space*, which is denoted as $\Omega$. All the results of the experiment, which are also in the $\Omega$ are called the sample point, denoted as $\omega$.
$$
\Omega = \{\omega|\omega ~ \text{are sample points of the experiment S} \}
$$


## Classical Model of Probability

Consider an experiment with a finite sample space $\Omega = \{\omega_1,\omega_2,...,\omega_m\}$. Suppose that there are numbers $p_1, p_2, ..., p_m$ with

$$ p_i \geq 0, ~ i = 1, 2,..., m, ~~ and ~~ \displaystyle{\sum\limits_{i=1}^m}p_i = 1 $$

and such that $p_i$ is the *probability* that $i$ is the outcome of the experiment $S$. Any set of possible outcomes of the experiment is called an event. If $P(A)$ denote the probability that event A occurs, then
$$
\begin{equation*}
P(A) = \sum_{i \in A} ~ p_i = \frac{\text{number of elements in event A}}{\text{total number of elements in sample space $\Omega$}}
\end{equation*}
$$

If these $p_1,p_2,...,p_m$ all exist with each other, this situation is called the **classical model of probability**. And we can easily deduce that
$$
\begin{equation*}
P(S) = \sum_{i} ~ p_i = 1
\end{equation*}
$$

For any event $A$, let $A^c$, called the complement of $A$, be the event containing all those outcomes in $S$ that are not in $A$. That is, $A^c$ occurs if and only if $A$ does not. Since

$$
\begin{align*}
1 &= \displaystyle{\sum_{i}} ~ p_i  \\
  &= \displaystyle{\sum_{i \in A}} ~ p_i + \displaystyle{\sum_{i \in A^c}} ~ p_i   \\
  &= P(A) + P(A^c)  \\
\end{align*}
$$
So it implies that

$$
\begin{equation*}
P(A^c) = 1 - P(A)
\end{equation*}
$$

For $ \varnothing = S^c $, we can obtain that

$$
\begin{equation*}
P(\varnothing) = 0
\end{equation*}
$$

Based on simple principle of set theory, 
$$
\begin{align*}
A \cup B &= A + B\bar{A} \\
A &= AB+A\bar{B} \\
  &= A(B+\bar{B})
\end{align*}
$$
for any events $A$ and $B$, we can write
$$
\begin{align*}
P(A \cup B) &= \displaystyle{\sum_{i \in A \cup B}} ~ p_i  \\
P(A)  &= \displaystyle{\sum_{i \in A}} ~ p_i  \\
P(B)  &= \displaystyle{\sum_{i \in B}} ~ p_i  \\
\end{align*}
$$

And **the addition theorem of probability for two events** can be written that
$$
\begin{align*}
P(A \cup B) &= P(A) + P(B) - P(A \cap B) \\

P(E_1 \cup E_2 \cup E_N) &= \sum_{i=1}^{N}P(E_i)-\sum_{i_1<i_2}P(E_{i_1}E_{i_2}) + \\
...&+(-1)^{r+1}\sum_{i_1<i_2<...<i_r}P(E_{i_1}E_{i_2}...E_{i_r}) \\
&+(-1)^{N+1}P(E_1E_2...E_N)
\end{align*}
$$

## Geometric Models of Probability

Consider $R^r$ denote a r dimension vector space
$$
R^r=\{(x_1,x_2,...,x_r)|x_i \in (-\infty,\infty),1 \leq i \leq r\}
$$
for subset $A$ of $R^r$,
$$
m(A)=\int_Adx_1dx_2...dx_r
$$
is volume of $A$. If $\Omega$ is the sample space of experiment $S$, when $\Omega \subset R^r$, the subset of $\Omega$ is *event*. So we can define the geometric models of probability:

If the volume of sample space $\Omega$ is positive, that is to say $m(\Omega) > 0$, and sample points are equiprobably in $\Omega$, for $A \subset \Omega$
$$
P(A)=\frac{m(A)}{m(\Omega)}
$$
is the probability of event $A$. And it has the similar properties like classical probability.

## Probability Space

In a sample space $\Omega$, the event $A$ is subset of $\Omega$. If $A$ satisfy that
$$
\text{$A$ is an event} \Rightarrow \text{$\bar{A}$ is also an event} \\
\text{$A_j$ is an event} \Rightarrow \text{$\bigcup_{j=1}^{\infty}A_j$ is also an event}
$$
that is to say, **after the complementary set operation and countable union operation, they are still in $\Omega$**, then the entire events in the $\Omega$ constitute a set $\mathcal{F}$, 
$$
\mathcal{F}=\{A|\text{$A$ is event},A \subset \Omega\}
$$
The $\mathcal{F}$ is called $\sigma$-domain($\sigma$-algebra), which is also called the **event domain** in the *probability*, including all the measurable events. There are three conditions of $\sigma$-algebra:

+ $\empty \in \mathcal{F}$
+ $A \in \mathcal{F} \Rightarrow A^c \in \mathcal{F}$
+ $A_1, A_2, \cdots, A_n \in \mathcal{F} \Rightarrow \bigcup\limits_{n=1}^{\infty}A_n \in \mathcal{F}$

From the measure theory view, all events in $\mathcal{F}$ will be assigned a value in $[0,1]$. Therefore, probability measure is a function from sample space $\Omega$ to $[0,1]$. If a function $P$ is defined in the domain $\Omega$, $A_1, A_2, ..., A_n$ are mutually exclusive events in $\mathcal{F}$, and satisfy:
$$
\left\{
\begin{align*}
&P(\Omega) = 1 \\
&P(A) \ge 0, \forall A \in \mathcal{F} \\
&P\left(\bigcup_{j=1}^{\infty}A_j\right)=\sum_{j=1}^{\infty}P(A_j)
\end{align*}\right.
$$
then such a function $P$ is a **probability measure** in $\mathcal{F}$, and a short name is **probability**. The combination $(\Omega, \mathcal{F}, P)$ is a **probability space**. The third condition is named as **conformable addition**. 

## Properties

From the 3 basic properties of probability space, we can deduce the below properties of probability:

1. $P(\varnothing)=0$
2. If $A_1, A_2, ..., A_n$ are mutually exclusive events, then

$$
P\left(\bigcup_{j=1}^{n}A_{j}\right)=\sum_{j=1}^{n}P(A_{j})
$$

​	which is called **finite addition**.

3. If $B \subset A$, then

$$
P(A-B) =P(A)-P(B) \\
P(A)>P(B)
$$

4. If $A_1,A_2,...,A_n$ are any events, then

$$
P\left(\bigcup_{j=1}^{n}A_j\right) \le \sum_{j=1}^{n}P(A_j) \\
P\left(\bigcup_{j=1}^{\infty}A_j\right) \le \sum_{j=1}^{\infty}P(A_j)
$$

Actually, from the conformable addition, we can deduce **the addition theorem of probability**:

+ $$ P(A \cup B) = P(A) + P(B) - P(A \cap B) $$

+ $$ P(A_1 \cup A_2 \cup A_3) = \sum\limits_{i=1}^{3}P(A_i)-\sum\limits_{i<j}P(A_{i}A_{j}) + P(A_{1}A_{2}A_{3}) $$

+ $$
  \begin{align*}
  P\left(\bigcup\limits_{i=1}^{n} A_i\right) &= \sum\limits_{i=1}^{n}P(A_i)-\sum\limits_{i<j}P(A_iA_j) + ... +
  (-1)^{k-1}\sum\limits_{j_i<j_2<j_k}P(A_{j_1}A_{j_2}...A_{j_k})+ ... +(-1)^{n-1}P(A_1A_2...A_n) \\
  &= C_{n}^{1}P(A_i)-C_{n}^{2}P(A_iA_j) ~ + ... +(-1)^{k-1}C_{n}^{k}P(A_1...A_k)+...+(-1)^{n-1}C_{n}^{n}P(A_1A_2...A_n) \\
  &= \sum_{k=1}^{n}(-1)^{k-1}C_{n}^{k}P(A_1A_2...A_k)
  \end{align*}
  $$

The third is called **Jordan formula**.

## Continuity

If $A_1 \subset A_2 \subset A_3 ... A_n \subset ... $, then they are called monotone increasing event sequence. And
$$
\bigcup_{i=1}^{\infty}A_i
$$
is the limit of $A_n$, denote as $\lim_{n \to \infty}P(A_n) = P(\bigcup_{i=1}^{\infty}A_i)$.

If $B_1 \supset B_2 \supset B_3 ... B_n \supset ... $, then they are called monotone decreasing event sequence. And
$$
\bigcap_{i=1}^{\infty}B_i
$$
is the limit of $B_n$, denote as $\lim_{n \to \infty}P(B_n) = P(\bigcap_{i=1}^{\infty}B_i)$.

## Frequency and Probability

If $A$ is one event in the experiment $S$ with $N$ times, then call *frequency* is
$$
f_N=\frac{\text{times of occurance of A in N experiment}}{N}
$$
if 
$$
\lim_{N \to \infty}f_{N}=P(A)
$$
exist, then call $P(A)$ is the probability of $A$ in experiment $S$. 

## Independence

If event $A$ and $B$ satisfy that $P(AB)=P(A)P(B)$, then call the events $A$ and $B$ are **independent**. 

If event $A$, $B$ and $C$ are **pairwise independent**, and satisfy that $P(ABC)=P(A)P(B)P(C)$, then call $A, B, C$ are **mutually independent**.

Here pairwise independence does not necessarily equal to mutually independence. Consider a dice with 4 faces and with number 1, 2, 3 and 4 on each face correspondingly. Define $A=\{1, 2\}, B=\{1, 3\}, C=\{1, 4\}$, then
$$
P(A)=\frac{1}{2},P(B)=\frac{1}{2},P(C)=\frac{1}{2}\\
P(AB)=P(BC)=P(CA)=\frac{1}{4}
$$
Obviously, $A, B, C$ are pairwise independent. However, they are not mutually independent, because
$$
P(ABC)=\frac{1}{4}\ne P(A)P(B)P(C)=\frac{1}{8}
$$
There are several conclusions:

+ $$P(\varnothing A)=P(\varnothing)P(A)  = 0$$
+ $$P(\Omega A) = P(\Omega)P(A) = 1$$
+ If $P(B)=1$, then $P(BA)=P(B)P(A)$, B is independent to A.
+ If $P(B) = 0$, then $P(BA)=P(B)P(A) = 0$, B is independent to A.

For events $A_i$, $\forall ~ 1 \leq j_1 < j_2 < ... < j_k \leq n$, if
$$
P(A_{j_1}A_{j_2}...A_{j_n})=P(A_{j_1})P(A_{j_2})...P(A_{j_n})
$$
then call them **mutually independent**. (The number of conditions are $2^n-1$.)

# Conditional Probability

## Conditional Probablity

The probability that event $A$ occurs given that event $B$ occurs is called the conditional probability, which is denoted as $P(A|B)$. The formula of conditional probability is that

$$
\begin{equation*}
P(A|B) = \frac{P(A \cap B)}{P(B)}
\end{equation*}
$$

This is because if the event $B$ happens, in order that the event $A$ happens, the occurrence must be a point in their intersection $AB$. Now that the event $B$ has occurred, it should be thought of the new sample space. And we can obtain the **multiplication theorem of probability**:

$$
\begin{align*}
P(AB) &= P(B)P(A|B)  \\
      &= P(A)P(B|A)
\end{align*}
$$

If the event $A$ is independent of the event $B$, $B$ is also independent of $A$, then $P(A|B) = P(A)$ and $P(B|A) = P(B)$. We get that
$$ P(AB) = P(A)P(B) $$

Generally, if $P(A_1A_2...A_{n-1})>0$, then
$$
P(A_1A_2...A{n})=P(A_1)P(A_2|A_1)P(A_3|A_1A_2)...P(A_n|A_1...A_{n-1})
$$

Here are tricky equations which help to understand conditional probability, given $P(ABC)>0$
$$
\begin{align*}
P(AB|C)=P(A|C)P(B|C) \Longleftrightarrow P(B|AC)=P(B|C) \\
\Longleftrightarrow P(A|BC)=P(A|C)
\end{align*}
$$

## Formula of Total Probability

**Formula of total probability** is an essential method to compute the probability of complex events whose *sample space* can be divided into small parts. We can get the probability of the original complicated event adding probabilities of these "small events". 

If events $B_1, ... , B_n$ constitute a *partition* of the sample space $\Omega$ , that is to say $B_i \cap B_j = \varnothing, ~ i \neq j, ~ i,j = 1,... n$ ; $P(B_i)>0, i = 1, ..., n$ and $ B_1 \cup ... \cup B_n = \Omega$, and if $A$ is any event in $\Omega$ , then
$$
P(A) = \sum_{i=1}^{\infty} P(B_i)P(A|B_i)
$$

## Bayes' Theorem

Based on the multiplication theorem of probability and the formula of total probability, we can get the famous ***Bayes' theorem***.

If events $B_1, ... , B_n$ constitute a *partition* of the sample space $\Omega$ , and if $P(A) > 0, P(B_i) > 0, i = 1, 2, ..., n$, then
$$
P(B_i|A)=\frac{P(B_i)P(A|B_i)}{\sum_{j=1}^{n}P(B_j)P(A|B_j)}
$$
$P(B)$ is also called the *prior probability*, which indicates the probabilities of all possible reasons for event $A$, and $P(B_i|A)$ is also called the *posterior probability*, which indicates the new recognition of probabilities of all possible reasons after the occurrence of event A.

More about Bayes' theory click the *Link*.

