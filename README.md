# This or That: Longevity Edition

**Choose better food alternatives.**

Pick 2 foods, choose a goal, and set your age and sex. The verdict comes from official food composition tables from 6 countries and regions, and every value is checked against its source.

Live site: https://cj-03-dev.github.io/This-or-That-v2/

## New in version 3

- 1,369 foods from 6 official tables: Japan, Brazil and West Africa join India, the United States and the United Kingdom, plus popular North American and European foods such as white bread, pizza, fries and diet cola
- Results tailored to your age (18 to 100) and sex, using official reference values
- A separate model for each goal, with longevity at the core of all of them
- Fairer to dairy and saturated fat, and ultra-processed foods lose points
- Better swaps for every food
- Light and dark mode (light by default)

## What it does

- Compares any 2 foods for 4 goals: longevity, weight loss, protein, and before a workout
- Shows a clear winner, scores out of 100, and up to 3 plain reasons (for example "More fibre: 7 g vs 2.7 g")
- Shows every nutrient per 100 g with the share of your own daily need, how each score was built, and where each value came from
- Suggests better swaps: foods that do the same job in a meal and score higher for your goal
- Search understands everyday names such as palak, dahi, natto and feijoada
- Stores nothing: no accounts, no cookies, no tracking

## The data

| Table | Country or region | Foods |
| --- | --- | --- |
| USDA National Nutrient Database for Standard Reference, Release 28 | United States | 561 |
| Indian Food Composition Tables 2017 (IFCT), ICMR-National Institute of Nutrition | India | 224 |
| UK Composition of Foods Integrated Dataset 2021 (CoFID), McCance and Widdowson | United Kingdom | 217 |
| Standard Tables of Food Composition in Japan 2020, 8th revised edition (MEXT) | Japan | 163 |
| Brazilian Food Composition Table (TACO), 4th edition, 2011, NEPA-UNICAMP | Brazil | 117 |
| FAO/INFOODS Food Composition Table for Western Africa 2019 (WAFCT) | West Africa | 87 |

Each food sits in the region where it is mainly eaten (natto in East Asia, feijoada in South America). Foods eaten all over the world, like apples or chicken, sit in the region of the table their numbers come from.

| Region | Foods |
| --- | --- |
| North America | 370 |
| South Asia | 297 |
| Europe | 276 |
| East Asia | 196 |
| South America | 122 |
| Africa | 94 |
| Southeast Asia | 10 |
| Middle East | 4 |

Every value, with its source and source code, is shown on the site under each comparison. The raw dataset export and the full verification workbook are kept outside this repository.

## How every value was verified

1. **Source re-read.** A separate program, written independently of the one that built the data, re-opened each original source file, found every food by its source code, redid every unit conversion and compared all 24 nutrient fields. 32,856 checks, 0 copying errors.
2. **Sense checks.** Every food was tested for impossible or unusual values, such as energy that does not match protein, fat and carbs, parts adding up to more than 100 g, sugar above total carbs, fatty acids above total fat, or vitamins a plant cannot contain. Every flag was investigated and explained or corrected.
3. **Cross-database check.** 361 comparisons with the same food in another table, across 304 foods: 284 agree, and the other 77 differences are explained (for example, Brazil's TACO measures cooked beans with their broth).

Results: 1,211 foods verified, 140 verified with a note, 18 corrected and documented. 11 foods were removed because their source figures do not add up, or the current table no longer gives enough to score them.

Corrections worth knowing about:

- The digital copy of IFCT lists ghee, vanaspati and 9 cooking oils at 0 kcal. Energy was calculated from fat at 9 kcal per g.
- IFCT's vitamin D is not used for any food: it lists vitamin D in plant foods at levels plants cannot reach (109 µg in pomegranate) and in egg white, which has none.
- For Japanese foods, carbohydrate follows the figure MEXT itself used for energy, except for fish, meat, eggs and milk, where MEXT's by-difference figure mostly reflects how protein and fat were measured.

## How the scores work

- **Longevity at the core.** The longevity score follows the Alternative Healthy Eating Index, the eating pattern most strongly linked to healthy ageing in a study of 105,015 people followed for up to 30 years (Tessier et al., Nature Medicine, 2025). Each food starts from its food type, then gains points for fibre, protein, long-chain omega-3, healthier fats and potassium, and loses points for free sugar, saturated fat, salt and industrial trans fat.
- **4 goals, one core.** Weight loss, protein and pre-workout scores are half longevity and half the goal itself.
- **Made for you.** Daily needs come from the NASEM Dietary Reference Intakes (via the NIH Office of Dietary Supplements), the Dietary Guidelines for Americans 2020 to 2025 and PROT-AGE. Nutrients that matter more at your age and sex earn extra points, and salt counts more from age 51.
- **Fair to dairy and fats.** Milk, yogurt and cheese carry no saturated fat penalty, butter, ghee and cream carry half, and only saturated fat above 10% of a food's calories counts (Hooper et al., Cochrane Review, 2020).
- **How processed it is.** Each food has a NOVA processing group; ultra-processed foods lose 6 points (Lane et al., BMJ, 2024).
- The maths is fixed: the same food and person always get the same score, and every point is listed.

## Ask about any food

The version hosted inside Claude also has a question box that answers only from the checked foods and cites each source code. It is not included in this GitHub copy.

## Limits

- Values are per 100 g as each table lists them, raw, cooked or as sold. Cooking changes them.
- Official tables do not record pesticide residues, antibiotics, or how a food was farmed, so the scores cannot account for them.
- Tables measure some nutrients differently. India's IFCT often reports about twice the fibre of USDA and CoFID for the same food.
- Missing values are never filled in. A missing value earns no points and loses none.
- General information only, not medical advice.

## Coming next

Picks for health conditions: high blood pressure, type 2 diabetes, PCOS, high cholesterol and fatty liver.

## Credits and licences

By Chirag Joshi: https://www.linkedin.com/in/cj-ceo-vm/

Built with Claude (Anthropic) as the project for Anthropic's AI Fluency course. I set the scope, picked the foods, chose the scoring approach and the design direction, and signed off every decision. Claude did the building and the checking at speed.

- IFCT 2017 values: ICMR-National Institute of Nutrition, via the open `ifct2017` data package (AGPL-3.0)
- USDA SR28: public domain
- CoFID 2021: contains public sector information licensed under the Open Government Licence v3.0
- MEXT 2020: Standard Tables of Food Composition in Japan 2020 (8th revised edition), Ministry of Education, Culture, Sports, Science and Technology
- TACO 2011: Tabela Brasileira de Composição de Alimentos, 4th edition, NEPA, State University of Campinas (UNICAMP)
- WAFCT 2019: Vincent A. et al. 2020. FAO/INFOODS Food Composition Table for Western Africa (2019). Rome, FAO. Licensed under CC BY-NC-SA 3.0 IGO; values derived from it on this site are shared under the same licence.
- Fonts: Funnel Display, Funnel Sans, Doto and Geist Mono (SIL Open Font License). Globe coastlines: Natural Earth (public domain).

Independent, non-commercial personal project. Not affiliated with or endorsed by ICMR-NIN, the USDA, the UK government, MEXT, NEPA-UNICAMP or FAO.
