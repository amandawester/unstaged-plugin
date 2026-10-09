---
name: guest-list
description: Add people to the couple's UNSTAGED guest list or update RSVPs, meals and dietary notes. Use when the user pastes or attaches a list of names, forwards replies from guests, asks who has not answered, or wants a count of who is coming.
---

## Add guests from a list

1. Call `get_wedding_overview` to learn the two partners' names and their order. `partner1` and `partner2` in the guest tools mean those two, in that order.
2. Call `list_guests` to see the groups already in use, so new guests join "Family" rather than a new group called "family members".
3. Turn the list into guests:
   - One guest per invited person. "Anna and Carl Berg" is two guests. "Anna Berg +1" is one guest with an unnamed plus-one; put a named partner in `plusOnes`.
   - `side`: whose guest it is. If the user says "my side" and it is unclear which partner you are talking to, ask once.
   - `group`: reuse an existing group where it fits.
   - Keep names as written, with their own spelling and capitals.
4. Call `add_guests` with up to 100 at a time. Names already on the list are skipped, not duplicated.
5. Say how many were added and how many were already there, and name the ones skipped. Do not repeat the whole list back.

## Update replies

For RSVPs, meal choices and dietary notes, find the guest with `list_guests` and call `update_guest` with only the fields that changed. When a name matches more than one guest, ask which one.

Dietary notes are for the caterer: write "no shellfish, allergy" rather than a sentence.

## Questions about the list

`list_guests` returns a summary and can be filtered by RSVP or group. For "who has not answered", list the names grouped the way the couple groups them, so they can see whom to chase.

Before the list is final, the couple may be working in Guest Ideas, the brainstorm of everyone they are considering. `list_guest_ideas` shows it. Do not move names from there to the guest list unless asked.

## Limits

Guests cannot be removed from here. If someone is no longer invited, say that removing is done in UNSTAGED, and offer to mark them as declined for now.
