---
name: vendors
description: Keep track of the couple's wedding vendors in UNSTAGED and help with the correspondence. Use when the user mentions a vendor they found, contacted, heard back from or booked (venue, photographer, florist, caterer, band, cake, hair and makeup), asks who is booked or still missing, or wants an enquiry, follow-up or reply to a vendor drafted.
---

## Keep the list current

1. Call `list_vendors` first. It shows each vendor's role, booking status, contact details and notes.
2. A vendor the couple has just found goes in with `add_vendor`: name, `role` in the same words the list already uses ("Florist", not "Flowers person"), contact details when given, and a short note on why they are interesting or who recommended them.
3. When something changes (contacted, replied, booked, turned down), call `update_vendor` with only the fields that changed. Put what was said in the note with a date, so the other partner can follow it.
4. Check for a vendor with the same name before adding, and update that one instead.

## Money belongs in the budget

A price a vendor quotes is not a note. Add it to the budget as a quote with `add_budget_row`, linked to the vendor with `vendorId`, as the quote-to-budget skill describes. When the couple books, mark the vendor as booked and the row as counted in the budget.

## What is missing

For "who do we still need", compare the roles in `list_vendors` with the budget categories from `get_budget` and the moments in `get_timeline`. Name the gaps that matter for this wedding, not a generic checklist: a daytime garden lunch does not need a lighting designer.

## Write to a vendor

Draft the message for the couple to send; nothing is sent from here. Take the facts from `get_wedding_overview` (date, place, guest count) and, for anyone who shapes how the day looks, two lines on style from `get_creative_direction`. Offer the Wedding Deck link from `get_deck` to attach. Keep an enquiry to what the vendor needs to answer: date, place, numbers, what is wanted, and one clear question.

## Limits

Vendors cannot be removed from here; that is done in UNSTAGED. Files such as contracts and quote PDFs are attached in UNSTAGED itself; from here you record the amounts and terms they contain.
