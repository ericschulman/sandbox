# structural-break-3-akm


This file tests for a structural break based on the concepts presented in [Andrews et al. 2020](https://economics.mit.edu/sites/default/files/2023-06/normmaxpaper.pdf). The specific challenge addressed testing for size of structural break, when the break date is unknown.

* I For $X_n$ I used F-statistic for a structural braek.
* Then $Y_n$ is and $\delta$ the magnitude of the break.
* $\theta$ corresponds to the date of the break.

The main assumption is that $ Y_n = \delta \sqrt{n} $ approaches a constant. As the sample size $ n $ increases, the influence of $ \delta $ diminishes, making $ E(Y_n) > 0 $ but it shrinks with the sample size. This characteristic is crucial because it is what leads to local asymptotic normality. 

If $ \sqrt{n} \delta$ did not approach a constant, then the statstics of interest will converge to a normal distribution. For additional context, see Andrews et al.'s working paper, which can be found [here](https://www.nber.org/papers/w25456).
 

$$ \|Y(\theta)\|^2 \approx \|\mu_Y(\theta)\|^2 + 2 \mu_Y(\theta)^T (Y(\theta) - \mu_Y(\theta))$$


Because the distribution of $(X_n, Y_n) $ are **locally linear behavior** around the null hypothesis in large samples, and exhibit  **local asymptotic normality**. If the conditions are not met, they follow a truncated normal distribution. For further insights, refer to Lemma 5.1 of the related literature, such as the paper available [here](https://projecteuclid.org/journals/annals-of-statistics/volume-44/issue-3/Exact-post-selection-inference-with-application-to-the-lasso/10.1214/15-AOS1371.full). When testing multiple restrictions on a jointly normal random variable (e.g., $x_1 > x_2, x_1 > x_3, x_1 > x_4,...$ and $y_1 > 0$), we address how restrictions on $X$ can impose constraints on $Y$.


# structural-break-covariates-idea-fixed


In this file, I look at what would happen both $X_n$ is $|\delta|$ and $Y_n$ is $|\delta|$. $\theta$ corresponds to the covariates we are using when detecting the break. Here are the restrictions being imposed.

In this file, I look at what would happen both $X_n$ is $|\delta|$ and $Y_n$ is $|\delta|$. $\theta$ corresponds to the covariates we are using when detecting the break. Here are the restrictions being imposed.

1. Start by simplifying the comparison:

$$\{ \hat{\theta} = \tilde{\theta} \} = \left\{ 
X(\tilde{\theta})^2 \geq X(\theta)^2, \forall \theta \in \Theta 
\right\} $$

2. Translate this into expressions involving random variables and covariance matrices:

$$ \left\{ 
\left(Z_{\tilde{\theta}}(\tilde{\theta}) + \Sigma_{XY}(\tilde{\theta}) \Sigma_Y(\tilde{\theta})^{-1} Y(\tilde{\theta}) \right)^2 \geq 
\left( Z_{\tilde{\theta}}(\theta) + \Sigma_{XY}(\theta,\tilde{\theta}) \Sigma_Y(\tilde{\theta})^{-1} Y(\tilde{\theta}) \right)^2, \forall \theta \in \Theta 
\right\}  $$

3. Reduce to the quadratic form:

$$ = \left\{ 
A(\tilde{\theta}, \theta) Y(\tilde{\theta})^2 + B(\tilde{\theta}, \theta) Y(\tilde{\theta}) + C(\tilde{\theta}, \theta) \geq 0, \forall \theta \in \Theta 
\right\}  $$

Given the quadratic inequality above, use the quadratic formula to solve for bounds on $ Y(\tilde{\theta}) $:

$$ G(\tilde{\theta}, \theta) = \frac{-B(\tilde{\theta}, \theta) - \sqrt{D}}{2A(\tilde{\theta}, \theta)} \quad \text{if } D \geq 0 \text{ and } A \neq 0 $$

$$ K(\tilde{\theta}, \theta) = \frac{-B(\tilde{\theta}, \theta) + \sqrt{D}}{2A(\tilde{\theta}, \theta)} \quad \text{if } D \geq 0 \text{ and } A \neq 0 $$


Where $ D $ is the discriminant given by $ D = B(\tilde{\theta}, \theta)^2 - 4A(\tilde{\theta}, \theta)C(\tilde{\theta}, \theta) $. Using the calculated $G(\tilde{\theta}, \theta)  $ and $ K(\tilde{\theta}, \theta) $, identify the interval over $ Y(\tilde{\theta}) $ that satisfies all conditions.

