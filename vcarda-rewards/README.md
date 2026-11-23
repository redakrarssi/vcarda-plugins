# Vcarda Rewards

Design a profitable loyalty rewards card from your menu, then open it in
Vcarda to save it. Works in Claude (Claude Code, Claude Desktop, Cowork and
claude.ai) and in ChatGPT.

## What it does

Share your menu or price list. The assistant ranks the best reward
candidates, asks for your profit margins, and builds a points or stamps card
where every reward costs about the same share of revenue: a cheap drink needs
few points, a main dish needs more. It recommends a quick first reward within
5 to 6 visits, can turn rewards 3 and up into combos, and explains the numbers
behind each threshold.

When the card is ready, one link opens it in the Vcarda program builder,
already filled in. You review it and click Save. No account is needed to
design a card.

Already on Vcarda? Connect your account to list your programs and update
their rewards from the chat. The assistant always shows the before and after
and asks before changing anything. It cannot see your customers, payments or
account settings.

## What's inside

- `skills/design-loyalty-rewards`: the guided design workflow.
- The Vcarda Rewards connector (remote MCP server at
  `https://mcp.vcarda.com/mcp`). Signing in uses
  your Vcarda account through OAuth; it is optional for designing a card.

## Install

Claude Code:

```
/plugin marketplace add redakrarssi/vcarda-plugins
/plugin install vcarda-rewards@vcarda-plugins
```

Claude Desktop and claude.ai: Customize, Plugins, Add marketplace, then
`redakrarssi/vcarda-plugins`.

ChatGPT: install Vcarda Rewards from the plugin directory.

## Try it

"Here is my cafe menu in QAR: Espresso 12, Latte 18, Cheesecake 25, Club
Sandwich 38. Build me a 3-reward points card, then give me the link to open it
in Vcarda."

## Privacy and support

- Privacy: https://www.vcarda.com/privacy#ai-assistant
- Terms: https://www.vcarda.com/terms
- Website and support: https://www.vcarda.com
