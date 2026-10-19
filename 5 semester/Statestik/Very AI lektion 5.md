## STAT Lecture 6: Confidence Intervals (CI) Notes

### Core idea

- **Point estimation:** a random sample X₁,…,Xₙ (iid) is used to estimate an unknown parameter θ. The estimate is θ̂ = h(x₁,…,xₙ).
- **Confidence interval:** an interval around θ̂ that contains the unknown θ with probability 100(1 − α)%, the _level of confidence_.
- **Common choices:** α = 0.01, 0.05 or 0.10, giving 99%, 95% or 90% CIs.
- **Trade-off:** a higher confidence level gives a wider CI. We want narrow intervals, but narrower means lower confidence.

### 1. CI for μ, normal distribution, σ² known

- **Model:** Xᵢ ~ N(μ, σ²), with μ unknown and σ² known.
- **Estimator:** X̄ ~ N(μ, σ²/n).
- **Pivot:** Z = (X̄ − μ) / (σ/√n) ~ N(0,1)
- **Starting point:** P(−z_{α/2} ≤ Z ≤ z_{α/2}) = 1 − α

|Type|Interval|
|---|---|
|2-sided|X̄ ± z_{α/2} · σ/√n|
|1-sided lower bound|[X̄ − z_α · σ/√n, ∞)|
|1-sided upper bound|(−∞, X̄ + z_α · σ/√n]|

For 1-sided intervals use z_α, not z_{α/2}, because all of α goes in one tail.

### 2. CI for μ, normal distribution, σ² unknown

- **Estimators:** X̄ ~ N(μ, σ²/n), and s² = 1/(n−1) · Σ(Xᵢ − X̄)², where (n−1)s²/σ² ~ χ²(n−1).
- **Pivot:** T = (X̄ − μ) / (s/√n) ~ t(n−1). Replacing σ with s changes the distribution from normal to t.
- **Starting point:** P(−t_{α/2}(n−1) ≤ T ≤ t_{α/2}(n−1)) = 1 − α

|Type|Interval|
|---|---|
|2-sided|X̄ ± t_{α/2}(n−1) · s/√n|
|1-sided lower bound|[X̄ − t_α(n−1) · s/√n, ∞)|
|1-sided upper bound|(−∞, X̄ + t_α(n−1) · s/√n]|

### 3. CI for σ², normal distribution

- **Model:** μ and σ² both unknown.
- **Pivot:** (n−1)s²/σ² ~ χ²(n−1)
- **Starting point:** P(χ²_{1−α/2}(n−1) ≤ (n−1)s²/σ² ≤ χ²_{α/2}(n−1)) = 1 − α
- **2-sided CI:** [ (n−1)s² / χ²_{α/2}(n−1) , (n−1)s² / χ²_{1−α/2}(n−1) ]
- The χ² distribution is asymmetric, so the interval is _not_ of the form estimate ± something.
- The subscript is the right-tail area: χ²_{α/2} is the quantile with α/2 probability above it. The bigger quantile goes in the denominator of the _lower_ bound.

### 4. CI for p, binomial distribution

- **Model:** X ~ B(n, p), with estimate p̂ = X/n.
- **Mean and variance:** E[p̂] = p and V[p̂] = p(1−p)/n.
- **CLT approximation:** for n·p ≫ 1 and n(1−p) ≫ 1, p̂ ≈ N(p, p(1−p)/n).
- **Pivot:** Z = (p̂ − p) / √(p(1−p)/n) ≈ N(0,1)
- **2-sided approximate CI:** p̂ ± z_{α/2} · √(p̂(1−p̂)/n)
- The unknown p in the standard error is replaced by p̂.

### 5. Prediction interval for the next observation, normal distribution

- **Model:** X₁,…,Xₙ iid N(μ, σ²). The next observation X_{n+1} ~ N(μ, σ²) is independent of the sample.
- **Predictor:** X̂_{n+1} = X̄.
- **Prediction error:** X̂_{n+1} − X_{n+1} ~ N(0, σ²(1 + 1/n)). The variance has two parts: σ² from the new observation itself and σ²/n from the uncertainty in X̄.
- **Pivot:** T = (X̂_{n+1} − X_{n+1}) / √(s²(1 + 1/n)) ~ t(n−1)
- **2-sided PI:** X̄ ± t_{α/2}(n−1) · √(s²(1 + 1/n))
- The slide header says "σ² known", but the formulas use s² and the t distribution, so this is the σ²-unknown case. If σ² really were known, you would use z_{α/2} · σ√(1 + 1/n).
- A prediction interval is always wider than the CI for μ because of the extra “1”.

### Quick reference: which distribution?

|Situation|Distribution|
|---|---|
|μ, σ² known|z (normal)|
|μ, σ² unknown|t(n−1)|
|σ²|χ²(n−1)|
|p (large n)|z (normal, approximate)|
|Next observation (σ² unknown)|t(n−1)|