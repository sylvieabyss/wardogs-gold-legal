# WARDOGS Gold

I made WARDOGS Gold so you can check the game's gold price from Discord. I host and maintain the bot, and you can invite it to your own server. This is mainly for community / clan servers.

The current price appears in the bot's status, with the percentage change when there's enough history. If you just want to keep an eye on that, there's nothing else to set up.

You can also check prices with slash commands. If your server wants daily posts or price alerts, your staff can choose a channel and an optional role to ping. **Notifications are off by default, and the bot never sends DMs.**

— Sylvie Abyss

## Adding the bot

Add WARDOGS Gold using its Discord invite, https://discord.com/oauth2/authorize?client_id=1555681704033656902 then check its status or run `/gold`.

In channels where you want to use commands or receive posts, give it **View Channels**, **Send Messages**, and **Embed Links**. It doesn't need Administrator or excessive perms.

I take care of hosting and updates. Your server staff only need to configure the notifications they want, if any.

## Commands

| Command | What it does | Who can use it |
| --- | --- | --- |
| `/gold` | Shows the current gold price and its source status. | Everyone |
| `/gold-history` | Shows recent prices. Defaults to 7 quotes, with up to 90 available. | Everyone |
| `/gold-convert` | Works out how many bars your cash can buy, or what a number of bars will cost. | Everyone |
| `/health` | Checks whether the tracker and its price sources are working. | Everyone |
| `/gold-config` | Shows your server's notification settings and active alert count. | Staff with Manage Server |
| `/gold-setup` | Sets up optional daily posts in a channel. | Staff with Manage Server |
| `/gold-setup-off` | Turns daily posts off. | Staff with Manage Server |
| `/gold-alert` | Creates a channel alert for a chosen price. | Staff with Manage Server |
| `/gold-alerts` | Lists your server's active alerts. | Staff with Manage Server |
| `/gold-alert-delete` | Removes an active alert by its ID. | Staff with Manage Server |

A few examples:

```text
/gold
/gold-history quotes:30
/gold-convert cash:1000000
/gold-convert bars:5
```

For conversions, enter either `cash` or `bars`. The history option counts recorded quotes, so 30 quotes won't always mean 30 consecutive days.

Staff settings and confirmations are only shown to the person using the command.

## Optional daily posts

If you'd like new prices posted in a channel, use:

```text
/gold-setup channel:#gold-market announcements:true
```

Choose a `mention_role` if you want a role ping. Leave it blank for a post without a ping. The role needs to be mentionable.

Add `post_current:true` if you want the current price posted straight away. If the bot can't verify a current price yet, it will tell you and wait until it can. You can't use this option with announcements turned off.

Use `/gold-config` to check your settings and `/gold-setup-off` to turn daily posts off. The status and price commands will keep working.

**Turning off daily posts doesn't delete separate price alerts.** You can manage those with `/gold-alerts` and `/gold-alert-delete`.

## Optional price alerts

Staff can set an alert to post when gold reaches a chosen price:

```text
/gold-alert channel:#gold-market direction:At or below price:400000
```

Choose **At or below** or **At or above**, enter the cash price per bar, and select a channel. As with daily posts, `mention_role` is optional. No role selected means no ping.

Each alert sends once, then leaves the active list. The bot won't create an alert if the current verified price already meets the condition, or if the same alert already exists for that channel. The default limit is 20 active alerts per server.

To remove one, find its ID with `/gold-alerts`, then use:

```text
/gold-alert-delete alert_id:1
```

If you want to change an alert's role, delete it and create it again. If a post fails, the bot retries in the same channel. It won't send a DM or move the alert somewhere else.

Notifications only mention a role your staff explicitly chose. They never ping individual users or @everyone. If the chosen role is deleted or stops being mentionable, the post goes out without a ping.

## Where the prices come from

The bot uses [MetaForge](https://metaforge.app/wardogs/market) as its main source and [WardogStats](https://wardogstats.app/gold) for fallback data and dated history.

WardogStats also gets its prices from MetaForge, so these aren't two independent checks against the game. **If you need to be certain before buying or selling, check the price in WARDOGS itself.**

The bot checks every 15 minutes normally, every minute around midnight UTC, and every five minutes while it's waiting for a current price or verification.

If a source is down, the bot may show the last known price marked as stale. If the sources disagree, it marks the price as needing verification and pauses notifications. If there's no usable price at all, it says so. Alerts and daily posts wait for a current usable price.

## If something isn't working

- **No daily posts?** They're off by default. Check `/gold-config` and make sure the bot can view and send messages in your chosen channel.
- **No role ping?** Check that you selected a role and made it mentionable.
- **Can't change settings?** You'll need Manage Server permission.
- **Price is stale or waiting for verification?** Run `/health` to check the sources. Notifications resume when a current price is available.
- **An alert is missing?** Alerts are removed from the active list after they send. Deleting their channel also removes them.

Discord or source outages can delay updates and notifications.

## Recent updates

Version 1.1.1 updates the project's licensing, privacy police and terms of service. The bot's features are unchanged from 1.1.0.

Personal alerts have been replaced with optional channel alerts managed by server staff. Old personal alerts were removed, while price history and existing daily-post settings were kept.

## Privacy and terms

The bot's original code and documentation are proprietary. You're welcome to invite and use the bot I host, under its [Terms of Service](TERMS.md). Copying, changing, redistributing, or hosting the software yourself requires written permission, except where an existing license or the law allows it.

See the [proprietary notice](LICENSE) and [Privacy Policy](PRIVACY.md) for more details.

WARDOGS Gold is my independent community project. It isn't affiliated with or endorsed by BULKHEAD, Team17, Discord, MetaForge, or WardogStats.

Made & maintained by Sylvie Abyss - sylvie@allworldsinteractive.com