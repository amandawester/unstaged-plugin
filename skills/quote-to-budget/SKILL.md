---
name: quote-to-budget
description: Add a vendor's quote or a committed cost to the couple's UNSTAGED wedding budget, or compare quotes. Use when the user pastes or attaches a quote, estimate, invoice or vendor email (florist, caterer, photographer, venue, cake, band), says what something will cost, or asks which option is the better deal.
---

The budget in UNSTAGED is made of categories, and each category holds rows. A row is either a quote (kept for comparison, not counted) or counted in the budget (the couple has decided on it). Keeping that difference right is the point of this skill.

## Add a quote

1. Call `get_budget` first. It gives the budget's currency, the category names, and the rows already there.
2. Read from the quote: who it is from, the total, and what the total includes. Use the total the vendor states. If the quote only gives a price per person or per item, multiply by the guest count from `get_wedding_overview` and say that you did.
3. If the quote is in another currency than the budget, do not convert silently. Say what the amount is in the quote's currency and ask what to enter.
4. Pick the category by what is being bought, not by the vendor's name: a bakery's dessert table belongs with the cake, not with food and drinks. Ask only when two categories fit equally well.
5. Check the rows in that category. If the same vendor and scope is already there, offer to update that row with `update_budget_row` instead of adding a second one.
6. Call `add_budget_row` with:
   - `name`: vendor and scope, e.g. "Bloom Studio · ceremony + tables"
   - `amount`: the total, as a number in the budget's currency
   - `covers`: up to six short tags for what is included, in the vendor's own terms ("ceremony arch", "12 tables", "delivery", "tax")
   - `note`: what is excluded, the deposit and its due date, or how long the quote is valid
   - `vendorId`: when the vendor is in `list_vendors`
   Leave `countedInBudget` out unless the couple has said they are going with this vendor. A quote that is counted by mistake makes the budget look spent.
7. Reply in two or three lines: where the row went, the amount, what it covers, and that it is saved as a quote. Mention anything the quote leaves out that the other quotes in the category include.

## Compare quotes

Read the rows in the category from `get_budget` and compare what each one covers, not only the amounts. A quote that includes delivery and setup is not more expensive than one that leaves them out. Say plainly which costs are missing from the cheaper option.

## When they decide

When the couple chooses, call `update_budget_row` with `countedInBudget: true` on that row, and offer to mark the vendor as booked with `update_vendor`. Leave the other quotes as they are; the couple removes rows themselves in UNSTAGED.

## Limits

Nothing can be deleted from here. Payments already recorded are never changed, and an amount cannot be set below what has been paid. If the user asks for either, say so and point them to the budget in UNSTAGED.
