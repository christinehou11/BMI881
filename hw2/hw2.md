## 1. If a test has sensitivity = 80% and specificity 80% and the prevalence of the disease is 9/100000, what is the positive predictive value (aka “precision”) of the test?

Define disease prevalence be $p = 9/100000$. Let D mean having the disease and + mean a positive test. Precision is $ \mathrm{PPV}=P(D\mid +)$. By Bayes’ theorem,

$$
P(D\mid +)=\frac{P(+\mid D)P(D)}{P(+)} = \frac{P(+\mid D)P(D)}{P(+\mid D)P(D)+P(+\mid D^c)P(D^c)}.
$$

Substituting the definitions,

$$
P(+\mid D)=\mathrm{Sensitivity},\qquad
P(+\mid D^c)=1-\mathrm{Specificity},\qquad
P(D)=p,
$$

Therefore

$$
\mathrm{PPV}
=
\frac{\mathrm{Sensitivity}\times p}
{\mathrm{Sensitivity}\times p+(1-\mathrm{Specificity})(1-p)}
=
\frac{0.8(9/100000)}
{0.8(9/100000)+0.2(1-9/100000)}
\approx 0.00036.
$$

Based on the result, only about 0.036% ($\approx 1/2779$) positive results would be a true positive. Equivlently, among 100000 people, we would have 7.2 true positives and 19,998.2 false positives.

## 2. Suppose sensitivity = specificity. What would they have to be to achieve positive predictive value = 50% when prevalence is 9/100,000?

Suppose sensitivity & specificity = $s$. To achieve $\mathrm{PPV}=0.5$,

$$
\frac{sp}{sp+(1-s)(1-p)}=\frac{1}{2} \quad\Longrightarrow\quad sp=(1-s)(1-p).
$$

Expanding and simplifying,

$$
sp=1-p-s+sp
\quad\Longrightarrow\quad
s=1-p =1-9/100,000=99.991\%.
$$

## 3. Comment on these results in relation to the precision values provided in Table 2 of Wang et al. (2019)

The paper included 1829 cases and 7665 controls. The resulting sample case proportion was $
\frac{1829}{1829+7665}\approx 19.3\%$, and obviously, this value is higher than the population disease frequency here. For all models, $p=9/100000=0.00009$.

**Combined model:** sensitivity = 83.1%, specificity = 82.3%.

$$

\mathrm{PPV}
=
\frac{0.831(0.00009)}
{0.831(0.00009)+(1-0.823)(0.99991)}
\approx \boxed{0.0422\%}.

$$

**Diagnosis-only model:** sensitivity = 79.6%, specificity = 71.2%.

$$
\mathrm{PPV}
=\frac{0.796(0.00009)}
{0.796(0.00009)+(1-0.712)(0.99991)}
\approx\boxed{0.0249\%}.
$$

**Medication-only model:** sensitivity = 81.7%, specificity = 78.4%.

$$
\mathrm{PPV}
=\frac{0.817(0.00009)}
{0.817(0.00009)+(1-0.784)(0.99991)}
\approx\boxed{0.0340\%}.
$$

Therefore, we could have:

| Input features | Table 2 | Here |
|---|---:|---:|
| Diagnosis only | 44.3% | 0.0249% |
| Medication only | 48.8% | 0.0340% |
| Diagnosis and medication | 57.1% | 0.0422% |

This corresponds to approximately 1 true case per 2367 positive predictions. Thus, the reported precision of 57.1% cannot be directly interpreted as the probability of disease following a positive prediction in the general population. A high AUROC does not by itself guarantee a high PPV when the disease is rare.

The overall sample case proportion and mean sensitivity/specificity do not exactly reproduce the reported precision. The table shows the averages across cross-validation folds, and averaging nonlinear quantities can produce discrepancies. 