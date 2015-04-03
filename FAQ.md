**How is MYA (Million Years Ago) deduced?**

To deduce MYA, a neutral mutation rate is required. Although there is a debate on non-neutral evolution at synonymous sites (http://www.nature.com/nrg/journal/v7/n2/abs/nrg1770.html), Ks is widely believed to be a approximation of neutral mutation rate and its unit is substitutions per site.

The commonly adopted estimate of mutational rate is 1.5×10e−8 substitutions per site per year in _Arabidopsis_ (http://www.ncbi.nlm.nih.gov/pubmed/16632643; http://www.ncbi.nlm.nih.gov/pubmed/11018155). Since Ks estimated by KaKs\_Calculator is a divergence between a pair of sequences, so that MYA = Ks / 2 / (1.5×10e-8).

Here is a paper related to this estimation at http://www.ncbi.nlm.nih.gov/pmc/articles/PMC1475497/pdf/tpc1801339.pdf.

**What is divergence time estimated by KaKs\_Calculator?**

Divergence time estimated by KaKs\_Calculator is a weighted average of synonymous substitution rate and non-synonymous substitution rate. It should be noted that it can not be used as neutral mutation rate.

**What values are used for the fisher exact test and what is the null hypothesis?**

The fisher exact test is to built a 2 × 2 contingency table using the numbers of synonymous and nonsynonymous substitutions (Sd and Nd) and the numbers of synonymous and nonsynonymous sites (S and N) and to examine the significance of the substitution and site between the two classifications (synonymous and nonsynonymous).

Therefore, its null hypothesis is Sd/S = Nd/N. Since Sd/S approximates Ks and Nd/N approximates Ka (the observed substitutions are less than the real ones, so it is only after correcting multiple substitutions that Nd/N and Sd/S could represent Ka and Ks, respectively), its null hypothesis also means neutral mutation. Reject the null hypothesis if Sd/S is singificantly greater (negative selection) or smaller (positive selection) than Nd/N, as indicated by small P-value (e.g., <0.05).