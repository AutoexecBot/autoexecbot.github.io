# Name Filter

Name filtering is used to ban chatters and new followers with offensive names that may not match your community guidelines for your channel.  It is an optional feature and you are not required to use it in your channel.  It provides the ability to add and remove name filters and allows for users to be whitelisted, if their name is caught by an over-eager filter.  The filters use a custom [filter syntax](./filtersyntax.md) designed for AutoexecBot to allow for flexible matching against phrases.

All of the commands listed on this page are restricted to usage by the channel broadcaster and moderators only.

> ⚠ There's currently no way to list all of the existing filters.  This is a feature that will be added in the future once the website is available.

## Subcommands

The name filter functionality uses a series of subcommands to allow for configuration, which are documented below.

### Add a new filter

> **Usage**
>
> `!namefilter add [filter]`

This subcommand is used to add a new filter to the name filters.  The `filter` parameter is required and follows the [filter syntax](./filtersyntax.md) outlined in the next section.

### Remove an existing filter

> **Usage**
>
> `!namefilter remove [filter]`

This subcommand is used to remove an existing filter from the name filters.  The `filter` parameter is required and follows the [filter syntax](./filtersyntax.md) outlined in the next section.

### Adding a user to the name whitelist

> **Usage**
>
> `!namefilter allow [name]`

This subcommand is used to add the given username to the whitelist of allowed users.  The `name` parameter is required and must be an exact match for the name of the user, however the name is not case sensitive.

This command will also unban the user if they had been banned.

### Removing a use from the name whitelist

> **Usage**
>
> `!namefilter allow [name]`

This subcommand is used to remove the given username from the whitelist of allowed users.  The `name` parameter is required and must be an exact match for the name of the user, however the name is not case sensitive.

This command will also ban the user if they have not been previously banned.