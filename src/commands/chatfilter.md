# Chat Filter

Chater filtering is used to moderate chat messages that may not match your community guidelines for your channel.  It is an optional feature and you are not required to use it in your channel.  It provides the ability to add and remove chat filters and setting the level of moderation to apply to the message.  The filters use a custom [filter syntax](./filtersyntax.md) designed for AutoexecBot to allow for flexible matching against phrases.

All of the commands listed on this page are restricted to usage by the channel broadcaster and moderators only.

> ⚠ There's currently no way to list all of the existing filters.  This is a feature that will be added in the future once the website is available.

## Subcommands

The chat filter functionality uses a series of subcommands to allow for configuration, which are documented below.

### Add a new filter

> **Usage**
>
> `!chatfilter add (moderation level) [filter]`

This subcommand is used to add a new filter to the chat filters.  The `filter` parameter is required and follows the [filter syntax](./filtersyntax.md) outlined in the next section.  The `(moderation level)` parameter is optional, defaulting to clearing the individual message from chat and can be configured as follows:

* `--timeout` - Times the user out for the default 10 minutes
* `--timeout=[duration]` - Times the user out for the specified duration in seconds
* `--ban` - Bans the users from chat

Some example uses:

* `!chatfilter add --ban KEKW` - Bans any user that says `KEKW` in chat
* `!chatfilter add --timeout KEKW` - Times out any user that says `KEKW` in chat for 10 minutes
* `!chatfilter add --timeout=300 KEKW` - Times out any users that says `KEKW` in chat for 300 seconds (5 minutes)
* `!chatfilter add KEKW` - Clears any individual messages containing `KEKW` from chat

### Remove an existing filter

> **Usage**
>
> `!namefilter remove [filter]`

This subcommand is used to remove an existing filter from the chat filters.  The `filter` parameter is required and follows the [filter syntax](./filtersyntax.md) outlined in the next section.
