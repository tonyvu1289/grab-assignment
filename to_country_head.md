# Executive Brief — Super-Combo Voucher Pilot (HCMC)

**To:** Country Head, Grab Vietnam
**From:** Data Science, VN
**Date:** 2026-05-27
**Subject:** Hanoi rollout decision for Super-Combo Voucher

## Context first
Gross GMV in HCMC went up during the promotion window. That spike is real in the raw data. At the same time, rainfall increased during the promotion. Rain can increase GrabFood demand and reduce GrabBike demand, so part of the spike can come from weather, not the voucher.

## Naive read of promo impact (rain-adjusted, HCMC vs Da Nang)
- **GrabFood:** +35.7% vs counterfactual.
- **GrabBike:** +8.7% vs counterfactual.

Bootstrap 95% CI (2,000 resamples of daily values):
- **GrabFood:** mean 0.358, CI [0.255, 0.469]
- **GrabBike:** mean 0.088, CI [0.001, 0.181]

## If you want to roll out to Hanoi now, do it only if
- We accept that current evidence is positive for both services, but the estimates are still rain-adjusted and naive.
- We are comfortable with a **partial rollout** (GrabFood-only or lower GrabBike subsidy).
- We agree to **tight measurement and stop/adjust rules** within 2–3 weeks.

## If not, the safer choice is to wait
- We can deliver a stronger readout in a few days with clearer controls.
- This reduces the risk of rolling out a bundle that lifts one service but hurts the other.
