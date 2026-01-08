# Optimizing-Care-Management-Prioritization-Under-Capacity-Constrains-Using-Healthcare-Claims-Data

## Final Results

This project evaluates a capacity-constrained care management prioritization framework, where only a limited number of members can be proactively engaged. Model performance is therefore assessed based on cost capture under fixed capacity (Top-K selection) rather than traditional prediction accuracy metrics.

## Cost Concentration

Healthcare spending in this population is highly concentrated. The top 5% of members account for approximately 40% of total annual spending, and the top 10% account for nearly 58%, confirming that targeted intervention has the potential to yield disproportionate impact.

## Baseline Prioritization Performance

A simple utilization-based prioritization strategy using inpatient and outpatient visit counts already performs substantially better than random selection.

For example:
  - Prioritizing the top 0.46% of members (K = 500) captures approximately 5.4% of total future spending, compared to ~0.45% under random   selection, representing more than a 10× improvement in resource efficiency.
  - This demonstrates that basic utilization signals contain meaningful ordering power for identifying high-impact members.

## Incorporating Length of Stay (Inpatient) Information

Naively incorporating average inpatient length of stay (LOS) into the prioritization score degraded performance, highlighting that LOS is a conditional and sparse variable that applies only to members with inpatient admissions.

To address this, average LOS was replaced with a binary long-stay indicator (≥7 days, conditional on having an inpatient admission). This refinement yielded modest but consistent improvements, particularly at moderate to larger capacity levels:

  - At K = 500, cost capture increased from 5.41% to 5.52%
  - At K = 2000, cost capture increased from 14.76% to 15.02%
  - At K = 5000, cost capture increased from 26.03% to 26.49%

These results indicate that LOS provides incremental value as a severity signal when applied conditionally, without destabilizing population-level rankings.

## Capacity Simulation Insights

Across all capacity levels evaluated (0.1%–4.6% of the population), both utilization-based strategies consistently outperformed random selection by a wide margin. Random selection closely tracked capacity proportion, while prioritization strategies captured 5–12× more cost than expected by chance.

Importantly, performance gains increased smoothly with capacity, suggesting stable ranking behavior rather than overfitting to a small subset of extreme cases.

## Key Takeaways
  1. Care management prioritization should be evaluated as a decision problem under capacity constraints, not solely as a prediction task.
  2. Simple, interpretable utilization-based rules already provide strong performance and meaningful business value.
  3. Severity indicators such as prolonged inpatient stays add value when applied thoughtfully and conditionally.
  4. Incremental improvements in cost capture translate to substantial real-world impact at scale.

Overall, this analysis demonstrates that decision-aware, capacity-constrained prioritization frameworks can substantially improve care management efficiency, even without complex machine learning models.
