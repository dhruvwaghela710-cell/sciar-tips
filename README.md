# Sciar Tips: CA2

**Live site (GitHub Pages):** https://YOUR-USERNAME.github.io/YOUR-REPO/
**Repository:** https://github.com/YOUR-USERNAME/YOUR-REPO

**My question:** Who carries the late-night work that Halloran's split rule pays nothing for, and can the least powerful person on staff say so safely?

- Staff view: [`app.html`](app.html) (signed in as Rafael, kitchen porter, S12)
- Landing page: [`index.html`](index.html) (for restaurant owners)
- Data: [`data/payouts.csv`](data/payouts.csv), [`data/takings.csv`](data/takings.csv), unchanged from the pack
- AI sessions: [`ai-log/`](ai-log/)

---

## Part 1: The people

**Internal: Aoife Rennick, CEO, Sciar.** Need: an alpha that works on the phones staff actually use: "Make it work on a phone. Nearly all restaurant staff only have phones." (`messages/04-aoife.md`).

**External: Rafael, kitchen porter, Halloran's.** Need: to understand his pay and ask about it without being identified: "the text has a long link and my phone screen is broken so i cannot read the page good." and "please dont say it was me who ask." (`messages/01-rafael.md`).

**Culture and accessibility:** Rafael's first language is Portuguese, he writes on a cracked screen, and his visa letter came from his employer. → The staff view has an EN/PT switch, large text and no long links, and concerns go to Sciar, anonymous by default.

## Part 2 and Part 3: notes and assumptions

- **Hidden figure:** 178.5 of Rafael's 527.5 hours (33.8%) were after 23:00 and earned no tip points. After Mehmet's last week (week 8), Rafael's average week went from 40.3 to 51.3 hours, but his average weekly tips only went from €55.83 to €58.09. His tips per hour fell from €1.38 to €1.13. Source: `data/payouts.csv`, `staff_id = S12`, columns `hours`, `hours_after_2300`, `tip_payout_eur`.
- **Second figure:** €9,004.69 of service charge went to the house over 12 weeks (`data/takings.csv`, `service_charge_paid_to = house`).
- **Checks I ran:** each week's `week_pool_eur` equals the sum of `card_tips_eur` for that week, to the cent. Every `points` and `tip_payout_eur` value reproduces from the split rule. Total paid out was €31,754.09 against a pool of €31,754.13, a 4-cent difference from rounding.
- **Groups of three or more:** only front of house (8 people), kitchen (5) and servers (5) are shown. Chefs (3) are left out too, because Kitchen minus Chefs would reveal the two kitchen porters.
- **Concern feature:** simulated with `localStorage` and labelled as simulated on the page. Rafael sees his own concerns, each with a timestamp and status.
- **Assumption:** the staff view is built for one person (Rafael). The "what-if" figure (€988.22) is labelled *inferred*: it keeps the same pool and points per hour, and counts hours after 23:00.
- **Assumption:** "paid every Monday" is Sciar's claim in the pack README. The data shows a payout calculated for every person every week, so the landing page claims only that.
- **Portuguese text** was drafted with AI and needs checking by a native speaker. The page says so.
- **Claims I left off the landing page:** "compliant with Irish tips law" (brief: no legal claims), "34% retention" and "only fully compliant platform" (`05-market-scan.md` gives no source), and "every cent" (the data shows a 4-cent rounding gap).

## Part 4a: Theory behind the build

**Leadership: Leader–Member Exchange (Graen and Uhl-Bien, 1995).** LMX explains the in-group of Declan, Niamh and the floor, and an out-group kitchen. Rafael depends on Declan through the visa letter, and his one question was closed with "the system" (`01-rafael.md`). **What it misses:** the gap is also a formal rule. Zero points after 23:00 moves value away from whoever closes the kitchen: kitchen staff work 11.5% of their hours after 23:00, against 2.6% for front of house (`payouts.csv`).

**Culture: organisational silence (Morrison and Milliken, 2000).** Niamh reads twelve quiet weeks as fairness (`03-niamh.md`), while Rafael kept quiet out of fear. Aoife's request to cut the concern feature (`04-aoife.md`) would build that silence into the product.

**Design:** because the silence comes from fear of the boss, concerns go to Sciar, anonymous by default. Owners see only topics raised by three or more people.

**Competitive advantage:** a tip pipe that hides its formula is easy to copy, but staff trust is not (Barney, 1991).

**Limit:** both theories assume voice is an individual choice. They miss migrant workers whose visa depends on the employer.

## Part 4b: Decision record

**Decision 1: request changed. Declan (`02-declan.md`) and Aoife (`04-aoife.md`) asked for the split rule to be shown only to owners.**

| Options | Criteria |
|---|---|
| A. Hide the rule (as asked) · B. Show everyone's hours and points · C. Show each person their own calculation, and colleagues only in groups of 3+ | Brief requires a hidden figure · Rafael's need to understand his own pay · Declan's fear of staff comparing hours · privacy |

**Decided by:** under A, Rafael cannot check his €54.46; B creates the comparisons Declan fears. C wins. **Underlying need served:** Declan wants no disputes between staff. No-one can see a named colleague's hours. **Would change my mind:** evidence that staff already share payouts, or that Declan's real worry is the rule itself being seen.

**Decision 2: AI suggestion rejected. The AI market scan (`05-market-scan.md`) recommended leading with "34% retention" and "only compliant platform".**

| Options | Criteria |
|---|---|
| A. Use both · B. Use them with "industry report" wording · C. Leave both out; use claims I can reproduce from `data/` | Brief: every number sourced in the pack, no legal claims · could the marker rebuild it? |

**Decided by:** the cited report isn't linked, and "only compliant" is a legal claim about competitors. Neither reproduces from `data/`. **Would change my mind:** the primary report, with method and sample, for the 34%. Nothing would bring back the compliance line.

**Bias I caught: Automation bias.** Initially, I trusted Claude's output without checking the original files. I later noticed missing quotes and had to restore the original CSV files. This taught me to verify AI-generated work against original sources.

## Part 4c: The Struggle (written without AI)
This project taught me about website development and the limitations of AI. I learned how to publish a website using GitHub Pages and fix errors, such as a missing quotation mark in a CSV file. This helped me realise how small mistakes can affect the entire website.

I also learned that AI can speed up development, but its output is not always reliable. Checking generated content against original files, testing the website and protecting private information are important. If I did this project again, I would test the website regularly as I build it and make frequent GitHub commits instead of leaving everything until the end. This hash is used for uploading CSV files to GitHub.
4b1a841.

## References

Barney, J. (1991) 'Firm resources and sustained competitive advantage', *Journal of Management*, 17(1), pp. 99–120.
Graen, G.B. and Uhl-Bien, M. (1995) 'Relationship-based approach to leadership: development of leader-member exchange (LMX) theory', *The Leadership Quarterly*, 6(2), pp. 219–247.
Morrison, E.W. and Milliken, F.J. (2000) 'Organisational silence: a barrier to change and development in a pluralistic world', *Academy of Management Review*, 25(4), pp. 706–725.
