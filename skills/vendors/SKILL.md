---
name: vendors
description: Keep track of the couple's wedding vendors in UNSTAGED and help with the correspondence. Use when the user mentions a vendor they found, contacted, heard back from or booked (venue, photographer, florist, caterer, band, cake, hair and makeup), asks who is booked or still missing, or wants an enquiry, follow-up or reply to a vendor drafted.
---

## Keep the list current

1. Call `list_vendors` first. It shows each vendor's role, booking status, contact details and notes.
2. A vendor the couple has just found goes in with `add_vendor`: name, `role` in the same words the list already uses ("Florist", not "Flowers person"), contact details when given, and a short note on why they are interesting or who recommended them.
3. When something changes (contacted, replied, booked, turned down), call `update_vendor` with only the fields that changed. Put what was said in the note with a date, so the other partner can follow it.
4. Check for a vendor with the same name before adding, and update that one instead.

## Documents on the vendor's card

Contracts, quotes, price lists and anything else a vendor sends belong under Documents on their card. Use `save_vendor_document` with the vendor's id and `kind` (`contract`, `quote` or `other`):

- It came as an email or a message: pass the full `text` exactly as written, with `from`, `subject` and `date`. It is saved as a PDF page. Do not summarise; this is the couple's record.
- There is a direct link to the PDF or image: pass `url`.
- The user attached a file to this chat: you cannot pass that file along. Call `save_vendor_document` with only the vendor id and `kind`, and give them the link it returns, unchanged. They drop the file there; it is valid for 20 minutes.

Give it a `name` the couple will recognise ("Signed contract", "Price list 2027"). Nothing already on the card is replaced. `list_vendors` shows what is there.

A quote is two things: the document on the card, and an amount in the budget. Do both when a vendor sends a price.

## Money belongs in the budget

A price a vendor quotes is not a note. Add it to the budget as a quote with `add_budget_row`, linked to the vendor with `vendorId`, as the quote-to-budget skill describes. When the couple books, mark the vendor as booked and the row as counted in the budget.

## What is missing

For "who do we still need", compare the roles in `list_vendors` with the budget categories from `get_budget` and the moments in `get_timeline`. Name the gaps that matter for this wedding, not a generic checklist: a daytime garden lunch does not need a lighting designer.

## Write to a vendor

Draft the message for the couple to send; nothing is sent from here. Take the facts from `get_wedding_overview` (date, place, guest count) and, for anyone who shapes how the day looks, two lines on style from `get_creative_direction`. Offer the Wedding Deck link from `get_deck` to attach. Keep an enquiry to what the vendor needs to answer: date, place, numbers, what is wanted, and one clear question.

## Limits

Vendors and their documents cannot be removed from here; that is done in UNSTAGED.
