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
It doesn't mean there is no way to calculate the true effect of the promotion. We will have to make some assumption, and calculate the true effect of the promotion based on that assumption.
1. Assumption: the effect of rainfall on net gmv is a decrease of x% in grabfood and this x is the same for both hcmc and da nang. The effect of rainfall and the promotion is linearly additive, which means the effect of rainfall is the same regardless of whether there is a promotion or not and vice versa.
- We can calculate the x based on the lift in grabfood gross gmv of da nang during the promotion period, then apply this x to hcmc grabfood gross gmv if there is no promotion, then compare the result with the actual hcmc grabfood gross gmv during the promotion period to see the true effect of the promotion on grabfood net gmv.
- We can do the same thing for grabbike to see the true effect of the promotion on grabcar and grabbike net gmv. Note that x% can be negative for grabbike, as rain can have a negative effect on grabcar net gmv.

