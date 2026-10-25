# Fitness Club Member Segmentation: Clustering and Personas (JASP)

Customer segmentation of 400 fitness-club members using model-based clustering, turned into three member personas with a retention strategy for each.

## Objective
Identify distinct groups of members from how committed they are, how they rate the club's facilities, and how they rate its classes, so the club can target each group differently.

## Data
- **400 survey respondents**, 21 variables: demographics (`Gender`, `Age`), four survey items each for equipment quality, class variety and facility cleanliness, plus `Years_of_Membership` and `Weekly_Usage_Hours`.
- Composite scores (`Equipment_quality`, `Class_Variety`, `Facility_Cleanliness`) were built from the item scores.

## Framework: three pillars
| Pillar | What it measures |
|---|---|
| 1. Intensity of commitment | Weekly usage, subscription duration, regularity of attendance |
| 2. Excellence of services and facilities | Equipment quality, cleanliness, maintenance standards |
| 3. Performance of the value proposition | Variety of courses, relevance of programs, scope of training |

## Method
1. **Model-based clustering** (JASP Machine Learning module). Inputs: `Years_of_Membership`, `Weekly_Usage_Hours`, `Equipment_quality`, `Facility_Cleanliness`, `Class_Variety`. Variables scaled; model chosen by BIC, maximum 3 clusters.
2. **One-way ANOVA** of `Weekly_Usage_Hours` across clusters (Type III sums of squares, omega-squared effect size).

## Results
- Model fit: AIC 1514.1, BIC 1573.9, R² = 0.23, average silhouette = 0.14.
- ANOVA: weekly usage differs strongly between clusters, F(2, 397) = 637.1, p < .001, omega-squared = 0.76.

| Persona | Members | Avg. weekly usage | Profile | Strategy |
|---|---|---|---|---|
| **1. Key members, strong commitment** | 209 | 11.6 h | Very high engagement, moderate view of facilities and value | Loyalty rewards, performance programs, maintain equipment standards |
| **2. Experience-oriented members** | 73 | 5.6 h | Moderate engagement, positive view of services, facilities and value | Maintain standards of excellence, expand training opportunities, referral incentives |
| **3. At-risk members, low engagement** | 118 | 4.1 h | Low engagement, poor view of services, facilities and value | Re-engagement campaigns, promotional offers, satisfaction surveys |

![t-SNE cluster plot] 
<img width="577" height="436" alt="image" src="https://github.com/user-attachments/assets/1a492c9d-ea67-4afc-8ed7-fe18db5af955" />

![Cluster means]
<img width="1302" height="535" alt="image" src="https://github.com/user-attachments/assets/d3f5768d-deb7-46e3-b53e-5f38cd33f4e7" />


## Takeaways
- Members split mainly by **how much they use the club**, and heavy users are the largest group (52%).
- The most satisfied members are not the heaviest users, and the least satisfied members use the club least, so facility and class quality are the most likely levers for re-engaging Persona 3.

## Limitations
- Weekly usage was also an input to the clustering, so the large ANOVA effect is partly built in. It describes the segments rather than independently testing them.
- The silhouette score (0.14) is low, so clusters overlap, as the t-SNE plot shows.
- Survey data, so results describe these respondents and may not generalize.

## Files
- `JASP_Project.jasp`: full analysis (open with [JASP](https://jasp-stats.org), built with v0.95.4)
- `images/`: exported plots

## Author
Manar Ben Salem. South Mediterranean University, Business Analytics.
