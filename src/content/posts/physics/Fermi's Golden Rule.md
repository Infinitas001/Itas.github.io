---
title: Fermi's Golden Rule
published: 2025-10-25
description: ''
image: ''
tags: [Golden Rule, Fermi]
category: 'Physics'
draft: false 
lang: 'ch_ZN'
---

参考
paper:
[Quasiparticle relaxation dynamics in superconductors with different gap structures](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.59.1497)
 blog：
 [读书笔记：费米黄金规则](https://zhuanlan.zhihu.com/p/627332500)

## 基本模型

### 描述
系统从没有被微扰的哈密顿量H的连续本征态$\ket{\phi_{i}}$到$\ket{\phi_{j}}$的跃迁速率/几率公式。本质上弱耦合近似下一阶含时微扰

### 推导
哈密顿量
$$
H=H_{0}+V(t)
$$
考虑态表示
$$
\ket{\Phi(t)}=\Sigma a_{n}(t) \ket{\phi_{n}} exp\left( -\frac{i}{\hbar}E_{n}t \right) 
$$
带入 ___Schrodinger function___，再左乘某定态$\ket{\phi_{m}}$，得到分量强度的随时间演化特征
$$
\frac{d}{dt}a_{m}(t)=-\frac{i}{\hbar} \Sigma_{n}V_{mn}a_{n}(t)exp(i\omega_{mn}t)
$$
其中$\omega_{mn}=\frac{E_{m}-E_{n}}{\hbar}$为Bohr频率

考虑近似：
1. 系统初态在$\ket{\phi_{n}}$
2. 弱耦合近似：系统演化到其他态的概率很小（弱耦合近似），因而上面等式右侧仅有$n$且$a_{n} \approx 1$

得到结论：如果系统演化到态$m$，则
$$
\frac{d}{dt} a_{m}(t)=-\frac{i}{\hbar}V_{mn}a_{n}(t)e^{i\omega_{mn}t}
$$
对应振幅：
$$
a_{m}(t)=-\frac{i}{\hbar}\int_{0}^{t}V_{mn}(\tau)e^{i\omega_{mn} \tau}  \, d\tau 
$$
从而，跃迁$n\to m$的几率
$$
P_{n \to m}=|\braket{\phi_{m}|\Phi(t)}|^2=|a_{m}(t)|^2=\frac{1}{\hbar^2}\left |\int_{0}^{t}V_{mn}(\tau)e^{i\omega_{mn}\tau}  \, d\tau \right|^2
$$
## 例子

### 阶跃势下的Fermi's Golden Rule
考虑
$$
V(t)=V\Theta(t)
$$
其中
$\Theta(t)$为 ___Heaviside___ 阶跃函数：
$$
\Theta(t)=
\left\{ 
\begin{aligned} 
&0 \ \ \ \ t<0 \\
&\frac{1}{2} \ \ \ \ t=0 \\
&1 \ \ \ \ t>0
\end{aligned}
\right.
$$
所以从$n\to m$，我们有：
$$
\begin{aligned}
P_{n \to m}&=\frac{1}{\hbar^2}|V_{mn}|^2|\int_{0}^t e^{i\omega_{mn} \tau} \, d\tau  |^2\\
&=\frac{1}{\hbar^2}|V_{mn}|^2 \left| \frac{\sin{\frac{\omega_{mn}t}{2}}}{\frac{\omega_{mn}}{2}} \right|^2  \\
&=\frac{2\pi t}{\hbar}|V_{mn}|^2 \delta(E_{m}-E_{n})
\end{aligned}
$$
最后一个式子使用狄拉克函数近似

从而，跃迁速率：
$$
\Gamma_{n\to m}=\frac{d}{dt}P_{n\to m}(t)=\frac{2\pi}{\hbar}|V_{mn}|^2 \delta(E_{m}-E_{n})
$$

### 与时间关联函数关系
(后续施工)

## 在超快光谱中的结论

- 首先考虑反射率的变化$\frac{\Delta R}{R_{0}}$的含义
$R_{0}$表示没有pump光，有probe光下的静态反射率
$\Delta R$表示引入pump后的差分反射率(___Differential Reflection___)变化（随时间）

注意，差分反射率指前后两次采样之间的反射率大小的差值（___一阶差分___）
这一数值与跃迁几率的倒数正比

- 其次，考虑e-ph作用的哈密顿量，即微扰来源：
$$
V\propto \hat{a}_{q}+\hat{a}^{\dagger}_{q}
$$
对于一个吸收过程$\hat{a}_{q}$，可以得到跃迁矩阵元：
$$
M_{mn}=\braket{m|V|n}\propto \braket{n_{q}-1|\hat{a}_{q}|n_{q}}   
$$
其中$n_{q}$表示在模式$q$上的声子数量
对于玻色子，这个数值结果为
$$
\braket{n_{q}-1|\hat{a}_{q}|n_{q}}=\sqrt{ n_{q} }
$$
- 最终，考虑到跃迁速率一方面对应强度正比于矩阵元平方，另一方面正比于差分反射率，所以有
$$
\frac{\Delta R}{R} \propto n_{q}
$$
