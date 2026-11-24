# Sciar Tips: CA2

**Live site (GitHub Pages):** https://priyanka050503.github.io/sciar-tips/
**Repository:** https://github.com/priyanka050503/sciar-tips

**My question:** Can the least powerful person at Halloran's see why their tips do not grow with their hours, and say so safely?

Pages: [index.html](index.html) (landing page, for restaurant owners) · [app.html](app.html) (staff view). Data: `data/` copied unchanged from the pack. AI sessions: `ai-log/`.

---

## Part 1: The people

| Stakeholder | Their words (file) | Need for my build |
|---|---|---|
| **Internal:** Aoife Rennick, CEO, Sciar | "Nearly all restaurant staff only have phones." (`messages/04-aoife.md`) | A staff view that works on a phone, and that she can show investors on Friday. |
| **External:** Rafael, kitchen porter, Halloran's | "i dont understand how they count it." / "please dont say it was me who ask." (`messages/01-rafael.md`) | To see how his pay is counted, and to ask about it without his manager knowing it was him. |

**Cultural difference and accessibility:** Portuguese is Rafael's first language, and "my phone screen is broken so i cannot read the page good." (`01-rafael.md`). So the staff view uses short sentences, large text and tap targets, no long links, a Portuguese switch, and accepts questions in any language.

---

## Part 4a: Theory behind the build

**Leadership: Leader-Member Exchange (Graen and Uhl-Bien, 1995).** LMX explains the case well. Niamh, the floor manager, is the only route for problems: "If someone has a problem they come to me." (`03-niamh.md`). Rafael is in the out-group. He depends on Declan for a visa letter, and when he asked Niamh in September he was told it was "the system" (`01-rafael.md`). The data shows what this exchange hides. The kitchen earned €2.98 per hour worked against €8.25 for the floor (`payouts.csv`, sum `tip_payout_eur` / sum `hours`, by team, 12 weeks). After Mehmet's last week (week 8), Rafael's average hours rose 27% (40.3 to 51.3) but his average payout rose only 4% (€55.83 to €58.09) (`payouts.csv`, `staff_id = S12`, weeks 1–8 vs 9–12). **What LMX misses:** the gap comes from the rule (0.25 points per hour, no points after 23:00), not only from relationships. A better exchange with Niamh would not change the arithmetic.

**Culture: organisational silence (Morrison and Milliken, 2000).** Niamh writes "Nobody has ever complained about the split." (`03-niamh.md`), yet Rafael raised it and then stopped. Silence here is not consent: it follows from a voice channel that runs through the people who hold power. The kitchen worked 269.5 of the 348 hours after 23:00 in the pilot (77%) (`payouts.csv`, sum `hours_after_2300` by team).

**Design choice:** because voice runs through the manager, questions in app.html go to Sciar, not to Niamh or Declan. The owner sees only a count, and only when three or more people have asked.

**Competitive advantage:** card payouts are easy to copy. Staff trust that is checked against data is rare and hard to imitate (Barney, 1991). If Sciar hides the rule from staff as Aoife asks, it becomes one more payments tool, open to the first public complaint.

**Limit:** both theories come from corporate settings. Neither models a migrant worker whose visa depends on his employer, which is the strongest reason for Rafael's silence.

---

## Part 4b: Decision record

**Decision 1: a request I changed: "Can we lose the 'raise a concern' idea from your sketch?" ... "Not for v1." (`04-aoife.md`), and Niamh's "please don't put a complaints button in the staff app" (`03-niamh.md`).**

| Options | Criteria | What decided it | What would change my mind |
|---|---|---|---|
| (a) Drop it. (b) Open, anonymous wall. (c) Private question to Sciar; owner sees counts only at 3 or more. | The brief requires a concern feature; Rafael's privacy; Niamh's fear of "anonymous digs"; Aoife's investor worry. | Only (c) meets all four. Silence in the data (Part 4a) means dropping it removes the only safe voice. | If Sciar could not answer a question within a week, a channel that leaves a trace but no reply would be worse than none. |

**Their underlying need:** Niamh wants problems solved without a public "moaning wall": no colleague ever sees a question. Aoife wants something investors trust: the feature is honest about being simulated, and the count is a signal owners can act on.

**Decision 2: an AI suggestion I rejected: make concerns anonymous.**

| Options | Criteria | What decided it | What would change my mind |
|---|---|---|---|
| (a) Anonymous. (b) Confidential: named to Sciar only. | Real protection, not apparent protection. | From week 9 Rafael is the only kitchen porter (`payouts.csv`, `role = kitchen porter`, weeks 9–12: 1 row each). A question about late kitchen-porter hours names him whatever the form says. Anonymity would be a false promise; confidentiality is honest. | Every role having three or more people each week. |

I also refused Declan's "Fully compliant with Irish tips law" and Aoife's "34% retention number": the first is a legal claim, the second has no traceable source (`05-market-scan.md`). I changed "Don't put the points table in front of staff." (`02-declan.md`): staff see their own points and team averages, never a colleague's row.

**Bias I caught: confirmation bias.** After reading Rafael, I expected Declan's "every cent of the card tips goes out on a Monday." to be false. When I ran the pool check, card tips equalled the pool in 12 of 12 weeks (€31,754.13). The claim was true, and the problem was the split, not missing money.

---

## Part 4c: The Struggle, without AI

<!-- WRITE THIS YOURSELF, 100–150 words, no AI. Include at least one commit hash. -->

---

## Assumptions

- "Floor team" = floor manager, servers, bar (8 people). "Kitchen team" = chefs, kitchen porters (5 people, 4 from week 9). Bar (2) and kitchen porter (1–2) are never shown alone.
- The app's staff picker is for the demo only; in production staff sign in and see only their own figures. All data are fictional.
- The "if late hours earned points" figure is inferred: it reruns the same week's pool with those hours added at the person's role rate. Colleagues would receive less.
- The pack README says 152 rows; an AI summary I used said 156. The file has 152: Mehmet has no rows in weeks 9–12.
- Payouts sum to €31,754.09 against a pool of €31,754.13: 4 cents of rounding, as the pack README notes.
- The Portuguese text was AI-translated and should be checked by a native speaker before real use.

## References

Barney, J. (1991) 'Firm resources and sustained competitive advantage', *Journal of Management*, 17(1), pp. 99–120.
Graen, G.B. and Uhl-Bien, M. (1995) 'Relationship-based approach to leadership: development of leader-member exchange (LMX) theory of leadership over 25 years', *The Leadership Quarterly*, 6(2), pp. 219–247.
Morrison, E.W. and Milliken, F.J. (2000) 'Organizational silence: a barrier to change and development in a pluralistic world', *Academy of Management Review*, 25(4), pp. 706–725.
