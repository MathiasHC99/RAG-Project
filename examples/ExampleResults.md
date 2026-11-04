# Example results

The tables summarize all vector results. Graph results include the matching recipes returned by the structured search. Sources use the `synthetic:` prefix.

## Question 1 — Creamy mushroom pasta

**Question:** “Give me a creamy pasta and mushroom recipe”

**Vector results:**

| Rank | ID | Recipe | Minutes | Score |
|---:|---|---|---:|---:|
| 1 | r001 | Creamy mushroom pasta | 20 | 0.8998 |
| 2 | r003 | Creamy chicken rice | 30 | 0.8176 |
| 3 | r011 | Peanut cucumber noodles | 16 | 0.8141 |
| 4 | r006 | Lemon herb couscous | 15 | 0.8075 |
| 5 | r010 | Roasted cauliflower bowls | 40 | 0.8058 |
| 6 | r007 | Tomato lentil stew | 35 | 0.7975 |
| 7 | r008 | Ginger tofu stir-fry | 22 | 0.7944 |
| 8 | r004 | Coconut chickpea curry | 25 | 0.7854 |
| 9 | r005 | Smoky black bean tacos | 18 | 0.7687 |
| 10 | r012 | Salmon and dill potatoes | 32 | 0.7646 |

Top result `r001`: creamy mushroom pasta with pasta, mushroom, oat cream, and olive oil. Source: `synthetic:r001`.

**Graph tool input:**

Screenshot: [Question 1 graph tool input](../Workflow%20Screenshots/Question%201%20graph%20tool%20input.png)

```text
restrictToCandidates: true
candidateIdsCsv: r001
requiredIngredientsCsv: pasta, mushroom
dietaryTagsCsv: [empty]
maxMinutes: 0 (no limit)
```

**Graph result:** `r001`, 20 minutes; ingredients: pasta, mushroom, oat cream, olive oil; dietary tag: vegan. Source: `synthetic:r001`.

**Agent response:**

> I found a perfect match for your request!
>
> **Creamy Mushroom Pasta**  
> Prep time: 20 minutes  
> Dietary tags: Vegan  
> Ingredients: Pasta, mushroom (sliced), oat cream, olive oil  
>
> **Instructions:** Cook the pasta according to package directions. Fry sliced mushrooms in olive oil. Add oat cream and simmer. Toss with the cooked pasta to create a rich, silky sauce.
>
> This is a comforting Italian-inspired dish that combines creamy oat milk sauce with earthy mushrooms over pasta. It's perfect for a quick, vegan-friendly dinner!

**Assessment:** Both searches returned `r001`, and the graph confirmed its ingredients and dietary tag. The data is synthetic.





## Question 2 — One-pot under 30 minutes

**Question:** “Find me one-pot recipes under 30 minutes”

**Vector results:**

| Rank | ID | Recipe | Minutes | Score |
|---:|---|---|---:|---:|
| 1 | r010 | Roasted cauliflower bowls | 40 | 0.7973 |
| 2 | r012 | Salmon and dill potatoes | 32 | 0.7956 |
| 3 | r011 | Peanut cucumber noodles | 16 | 0.7919 |
| 4 | r008 | Ginger tofu stir-fry | 22 | 0.7873 |
| 5 | r006 | Lemon herb couscous | 15 | 0.7873 |
| 6 | r005 | Smoky black bean tacos | 18 | 0.7867 |
| 7 | r007 | Tomato lentil stew | 35 | 0.7806 |
| 8 | r009 | Apple cinnamon oats | 12 | 0.7791 |
| 9 | r004 | Coconut chickpea curry | 25 | 0.7765 |
| 10 | r001 | Creamy mushroom pasta | 20 | 0.7756 |

**Graph results:** Six recipes met the 30-minute limit:

| ID | Recipe | Minutes | Ingredients | Source |
|---|---|---:|---|---|
| r009 | Apple cinnamon oats | 12 | oats, apple, cinnamon, water | `synthetic:r009` |
| r006 | Lemon herb couscous | 15 | couscous, lemon, parsley, olive oil | `synthetic:r006` |
| r011 | Peanut cucumber noodles | 16 | noodles, peanut butter, cucumber, lime, soy sauce | `synthetic:r011` |
| r001 | Creamy mushroom pasta | 20 | pasta, mushroom, oat cream, olive oil | `synthetic:r001` |
| r008 | Ginger tofu stir-fry | 22 | tofu, broccoli, ginger, soy sauce, oil | `synthetic:r008` |
| r004 | Coconut chickpea curry | 25 | chickpea, coconut milk, spinach, onion, curry powder | `synthetic:r004` |

All six graph results were tagged vegan. The graph data does not have a one-pot property.

**Graph tool input:**

Screenshot: [Question 2 graph tool input](../Workflow%20Screenshots/Question%202%20graph%20tool%20input.png)

```text
restrictToCandidates: true
candidateIdsCsv: r001, r004, r006, r008, r009, r011, r012
requiredIngredientsCsv: [empty]
dietaryTagsCsv: [empty]
maxMinutes: 30
```

**Agent response:**

> Here are my one-pot recipe recommendations under 30 minutes:
>
> **Apple Cinnamon Oats (12 minutes)** — Vegan. Oats, apple, cinnamon, and water. Simmer oats in water with diced apple and cinnamon until soft.
>
> **Lemon Herb Couscous (15 minutes)** — Vegan. Couscous, lemon, parsley, and olive oil. Prepare couscous, then mix with lemon, parsley, and oil.
>
> **Coconut Chickpea Curry (25 minutes)** — Vegan. Chickpea, coconut milk, spinach, onion, and curry powder. Fry onion and curry powder, add chickpeas and coconut milk, simmer, then stir in spinach.
>
> Apple cinnamon oats uses one pot. Lemon herb couscous is typically made in one pot. Coconut chickpea curry can be made in one pot. All three are quick vegan options under 30 minutes.

**Assessment:** All three recommendations are under 30 minutes and appear in the graph results. However, the graph only filters by time; it does not verify “one-pot.” The agent also omitted three other graph matches.





## Question 3 — Meat and potatoes

**Question:** “Find me some recipes with meat and potatoes”

**Vector results:**

| Rank | ID | Recipe | Minutes | Score |
|---:|---|---|---:|---:|
| 1 | r012 | Salmon and dill potatoes | 32 | 0.8505 |
| 2 | r007 | Tomato lentil stew | 35 | 0.8293 |
| 3 | r005 | Smoky black bean tacos | 18 | 0.8163 |
| 4 | r008 | Ginger tofu stir-fry | 22 | 0.8138 |
| 5 | r006 | Lemon herb couscous | 15 | 0.8114 |
| 6 | r011 | Peanut cucumber noodles | 16 | 0.8107 |
| 7 | r001 | Creamy mushroom pasta | 20 | 0.8058 |
| 8 | r004 | Coconut chickpea curry | 25 | 0.8013 |
| 9 | r002 | Fresh chickpea salad | 10 | 0.8009 |
| 10 | r010 | Roasted cauliflower bowls | 40 | 0.7980 |

**Graph result:** `r012`, Salmon and dill potatoes, 32 minutes; ingredients: salmon, potato, dill, lemon; no dietary tags. Source: `synthetic:r012`.

**Graph tool input:**

Screenshot: [Question 3 graph tool input](../Workflow%20Screenshots/Question%203%20graph%20tool%20input.png)

```text
restrictToCandidates: true
candidateIdsCsv: r012
requiredIngredientsCsv: potato, salmon
dietaryTagsCsv: [empty]
maxMinutes: 0 (no limit)
```

**Agent response:**

> I found one match with both salmon and potatoes in our recipes:
>
> **Salmon and Dill Potatoes**  
> Cook time: 32 minutes  
> Dietary tags: None (contains salmon)  
> Ingredients: salmon, potato, dill, lemon  
> Instructions: Boil potatoes until tender. Bake salmon until cooked through and serve with dill and lemon.  
> Description: A light, herby dinner with flaky salmon.
>
> This is the closest match to your request for meat and potatoes. The only recipe in our database that includes both ingredients together is the Salmon and Dill Potatoes dish. It's a Nordic-inspired meal that combines boiled potatoes with baked salmon, finished with fresh dill and lemon garnish.
>
> If you'd like more recipes with either meat or potatoes separately, I'd be happy to search for those!

**Assessment:** Both searches returned `r012`, which contains salmon and potatoes. Salmon is fish, not meat in the usual culinary meaning, so this is not a confirmed match for “meat and potatoes.” The answer should describe it as a fish alternative rather than the requested meat recipe.


