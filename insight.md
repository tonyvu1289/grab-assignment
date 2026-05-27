# Insight
1.  We see a lift in net gmv of Ho Chi Minh city(based on avg line) during the promotion peroid, which is epxected. However, there is also a)small lift in net gmv of Da Nang city, which make us a bit of concern about the cannibalization effect of the promotion. Is there any factor that make the overall net gmv increase, and how much? In the worst case, the promotion may actually decrease the overall net, but external factor keep it increase (but not as much as not having the promotion)?

![alt text](image.png)

2. We make a comparision of net gmv between different user segment accross different cities. Look like there is no significant difference between different user segment, which is intuitively something wrong. If the promotion is effective, we should see a lift in net gmv of voucher hunter much more higher than other user segment due to the fact that they are more price sensitive.

![alt text](image-1.png)

3. Rain is one of the most important factor that can affect the net gmv. During rain, people tend to use more grabcar, grabfood and avoid using grabbike. Unfortunately, we observe a lift in daily rainfall during the promotion period, which can make rainfall a confounding factor that can affect the net gmv. We need to control the rainfall factor to see the true effect of the promotion on net gmv.
![alt text](image-2.png)

4. HCMC gross gmv of grab bike is decrease during the promotion period, which is unexpected. This decline can be explained by high rainfall during the promotion period, which can make people avoid using grabbike, or the price was pushed up too much due to the rain.The negative effect of rainfall can be shadowing the positive effect of the promotion.
5. Grabcar gross gmv is increase during the promotion period, evenwhen promotion is not applied to it. This can be explained by the fact that grabcar is more comfortable and safer than grabbike during rain, so people tend to switch from grabbike to grabcar during rain. We can see not only hcmc but also da nang (which also have high rainfall) have a lift in grabcar gross gmv during the promotion period.
6. grab-food gross gmv of hcmc is improve during the promotion period. However, the lift in grab-food gross gmv of da nang during the promotion is observed. As we have known, there's a lift in rainfall during the promotion period in da nang and hcmc. Rain can be a confounding factor that can affect the net gmv of grab-food, as people tend to order more food delivery during rain. This gonna make it hard to see the true effect of the promotion on grab-food net gmv. We can argue the lift would not have been that much if there is no promotion.
![alt text](image-5.png)

# Calculate strategy 
It doesn't mean there is no way to calculate the true effect of the promotion. We will have to make some assumption, and calculate the true effect of the promotion based on that assumption.
## Naive approach
Because we only have 24-hour to reply, let do a dirty calculation first.  
Assumption: the effect of rainfall on net gmv is a decrease of x% in grabfood and this x is the same for both hcmc and da nang. The effect of rainfall and the promotion is linearly additive, which means the effect of rainfall is the same regardless of whether there is a promotion or not and vice versa.
Assumption: the pre-promotion trend is stable (or at least parallel) between HCMC and Da Nang for the same service type. The charts look stable by eye, but this is not formally tested and should be stated as a caveat.

**Step 1: Calculate rainfall effect from Da Nang (control city with no promotion)**
$$x_{\text{rain}} = \frac{\text{avg}(\text{gmv}_{\text{da nang}}^{\text{during promotion}}) - \text{avg}(\text{gmv}_{\text{da nang}}^{\text{pre promotion}})}{\text{avg}(\text{gmv}_{\text{da nang}}^{\text{pre promotion}})}$$

**Step 2: Apply rainfall effect to construct counterfactual for HCMC**
$$\text{gmv}_{\text{hcmc}}^{\text{counterfactual}} = \text{avg}(\text{gmv}_{\text{hcmc}}^{\text{pre promotion}}) \times (1 + x_{\text{rain}})$$

**Step 3: Calculate true promotion effect**
$$\text{promotion effect} = \frac{\text{avg}(\text{gmv}_{\text{hcmc}}^{\text{during promotion}}) - \text{gmv}_{\text{hcmc}}^{\text{counterfactual}}}{\text{gmv}_{\text{hcmc}}^{\text{counterfactual}}}$$

Result (GrabFood, gross GMV):
- Da Nang pre avg = 20,348.63 k VND, during avg = 29,219.20 k VND, so $x_{\text{rain}} = 0.43593$.
- HCMC pre avg = 75,583.00 k VND, during avg = 147,230.47 k VND.
- Counterfactual HCMC during promo = 108,531.87 k VND.
- Naive promotion effect = 0.35656 (about 35.7% uplift vs counterfactual).

Result (GrabBike, gross GMV):
- Da Nang pre avg = 3,311.56 k VND, during avg = 2,495.46 k VND, so $x_{\text{rain}} = -0.24644$.
- HCMC pre avg = 11,651.95 k VND, during avg = 9,543.00 k VND.
- Counterfactual HCMC during promo = 8,780.44 k VND.
- Naive promotion effect = 0.08685 (about 8.7% uplift vs counterfactual).

Combined naive results (gross GMV, HCMC vs Da Nang):
- GrabFood: +35.7% vs counterfactual (rain proxy $x_{\text{rain}} = 0.43593$).
- GrabBike: +8.7% vs counterfactual (rain proxy $x_{\text{rain}} = -0.24644$).

Bootstrap 95% CI (2,000 resamples of daily values):
- GrabFood: mean 0.358, CI [0.255, 0.469].
- GrabBike: mean 0.088, CI [0.001, 0.181].

- We can do the same calculation for grabbike to see the true effect of the promotion on grabcar and grabbike net gmv. Note that $x_{\text{rain}}$ can be negative for grabbike, as rain can have a negative effect on grabbike net gmv.
## diff in diff approach
Assumption: the net/gross gmv in any transformed way (log, percentage change, de-bias some variable, etc) of 3 city will have the paralel trend if there is no promotion.
