# Simultaneous parameter search and simulation

When designing a clinical trial, a key task is to demonstrate the
operating characteristics of the proposed design. This is especially
important for trials designed using Bayesian methods because such
methods do not have built-in type I error control like *p*-value
methods.

One approach for calibrating a Bayesian design to have type I error
control is via the prior distribution on the treatment effect parameter.
(The treatment effect doesn’t necessarily need to be a single parameter;
it could also be a function of several parameters. In this case, a prior
would be placed on the function of parameters.) For example, consider
the simplest setting where the treatment effect is a difference in
means. The model (which includes the expression for the conditional
variance) is

$$
\begin{aligned}
\text{trt} &= \left\\\begin{array}{ll}
1 & \text{active intervention}\\
0 & \text{placebo}\\
\end{array}\right. \\
E\[y|\text{trt}\] &= \beta\_0 + beta\_1 \text{trt}\\
V\[y|\text{trt}\] &= \sigma^2\\
\beta\_0 &\sim N(0,\theta\_{\beta\_0})\\
\beta\_1 &\sim N(0,\theta\_{\beta\_1})\\
\sigma &\sim \text{exponential}(\theta\_{\sigma}).
$$

The parameter *θ*<sub>*β*<sub>1</sub></sub> can be selected/calibrated
so that the trial has a type I error rate of 5%.

Type I error is inherently linked to the decision-making strategy for
the trial. The decision-making strategy is a rule or set of rules which
define a conclusive or reportable difference. In the setting of our
difference in means example, the Bayesian decision making quantity can
be the posterior probability of efficacy,
posterior *P*(*β*<sub>1</sub>&gt;0). The rule could be

$$
\widehat{\text{posterior } P(\beta\_1&gt;0)} \begin{array}{ll}&lt; 0.95 & \text{Not a conclusive difference}\\
\geq 0.95 & \text{Conclusive difference}
\end{array}
$$