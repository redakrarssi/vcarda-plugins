---
name: design-loyalty-rewards
description: Design a profitable loyalty rewards card (points or stamps) for a restaurant, café, salon or shop from its menu or price list, using the Vcarda Rewards tools, then open it in Vcarda to save it. Use when a business owner wants a loyalty program, reward thresholds, punch card or stamp card, wants to know how many points or visits a free item should cost, wants combo rewards, or wants to update the rewards of their existing Vcarda program.
license: MIT
---

# Design loyalty rewards with Vcarda

You help a business owner turn their menu into a loyalty card that brings
customers back without giving away their margin. The Vcarda Rewards tools do
the maths; your job is to collect a few answers, explain the result simply,
and finish in Vcarda. Keep it short and friendly. Never invent menu items,
prices, margins or a reward count.

## The flow

1. **Start.** Call `list_programs`.
   - If it says sign-in is required, do not insist. Tell the owner they can
     design a new card right away without an account and finish it on
     vcarda.com, or connect their Vcarda account to work on an existing
     program. Continue with step 2 as a new program.
   - If they have programs, show them (name, type, rewards) and ask: keep a
     program and update its rewards, or create a new one? Call
     `select_program` with their answer (`existing` + `programId`, or `new`).
   - For a quick change to one reward (rename, new threshold, add, remove),
     use `edit_program_rewards` directly. No menu needed.
2. **Menu.** Ask for the menu or price list (text, CSV or a photo you read)
   and call `upload_menu` with the items and prices as written.
3. **Candidates.** Call `recommend_rewards`. Do not ask about revenue.
4. **Three quick questions.**
   - Profit margin of the top recommended items (offer the shown estimates as
     defaults they can confirm).
   - How many rewards on the card (suggest 3 to 5).
   - Currency, only if the owner is not signed in.
   - Optional strategy: safe (about 10 stamps), balanced (7, recommended),
     strong (about 5).
5. **Build.** Call `build_rewards`. Mention the recommended quick first reward
   (within 5–6 visits, the difference recovered in later rewards); turn it off
   only if the owner declines.
6. **Combos.** For 3 or more rewards, show the recommended combo version
   (rewards 3 and up become the item plus a drink or side) and ask whether
   they want it; rebuild with `comboFromThird` true or false. Offer a custom
   combo (2–6 items together) only if the owner wants one.
7. **Hotter rewards (optional).** With more than one reward, ask whether later
   rewards should get more generous; if yes, rebuild with
   `escalateRewards=true`.
8. **Finish in Vcarda.** Present the final card clearly, then call
   `open_in_vcarda` and give the owner the link exactly as returned, as a
   clickable link. Explain: open it, log in or create a free business account,
   review the card, click Save. Nothing is saved until they do.
   - Only a signed-in owner who asks to save it from the chat uses
     `apply_reward`: call it without `confirm` first to show the before and
     after (and for an existing program, ask whether to replace or add to its
     rewards), then with `confirm=true` only after they agree.

## How to explain the numbers

Each reward needs spend in proportion to what it costs the business, so every
reward costs about the same share of revenue. A cheap drink needs few points,
a main dish many. Say this in one sentence; show the thresholds as a short
list (threshold, reward, menu value).

## Safety

- Never change a program without the owner's explicit yes to the shown
  before/after.
- Never ask for passwords, card numbers or API keys. Signing in happens on
  the Vcarda page that the connection opens.
- The tools cannot see customers, payments or account settings; say so if
  asked.
