# Southern Vermont Stays by Ozvermont

<img src="assets/logo.png" alt="Ozvermont Stays logo" width="128">

Find, price and book vacation stays in southern Vermont, from inn rooms to whole-house rentals, from your AI assistant.

Ozvermont runs a growing collection of places to stay in southern Vermont, near the Mount Snow and Stratton ski areas. Today it includes Deerfield Valley Inn, a bed and breakfast in West Dover, and Paradise Vermont, a whole-house chalet in Winhall with a hot tub and a pool.

This plugin connects Cursor and Grok Bot to Ozvermont's booking service, a remote MCP server run by the owner. It holds no code: it only points your assistant at the server. A new property shows up through the server's `list_properties` tool, without a plugin update.

## What you can do

- See every property: rooms, amenities, location, stay rules, policies, breakfast where a property serves it, and answers to common questions.
- Find open dates and see prices.
- Get an exact, itemized quote in US dollars, with the seller, the key terms and the cancellation rule.
- Book, with your approval: start a booking, add breakfast where a property offers it, pay on a secure Stripe card page or by US bank transfer, and follow the booking to the end.
- Send a request to the property, such as other dates or an early check-in, or cancel.

## Example prompts

```text
Where can I stay near Mount Snow this winter?
Is there a vacation home in southern Vermont with a hot tub for a family weekend?
Book a fireplace room at Deerfield Valley Inn for two next weekend, with breakfast on Saturday.
Book Paradise Vermont for six people for three nights from a Sunday about a month from now, at the refundable rate.
Give me the payment page for my booking.
What is the status of my Paradise Vermont booking?
Ask Deerfield Valley Inn if we can move our stay one week later.
Cancel my Deerfield Valley Inn booking.
```

## Install

**From the marketplace:** find "Southern Vermont Stays by Ozvermont" in the Cursor Marketplace and install it. Grok Bot uses the same plugins.

**By hand:** add the server to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "ozvermont-stays": {
      "url": "https://api.deerfieldvalleyinn.com/mcp"
    }
  }
}
```

The plugin needs no API key and no settings.

## Sign-in

- Browsing, open dates and quotes need no sign-in.
- Booking needs a sign-in. When a booking tool runs, your assistant opens our sign-in page. You enter your name, email and phone, then the one-time code we email you. There are no passwords.
- Sign-in uses OAuth 2.1 with PKCE. Your assistant registers itself as a public client; there is no client secret.
- An assistant's sign-in lasts 24 hours. Then you sign in again.
- You must be 18 or older to book.

If your assistant cannot sign in during a chat, use `https://api.deerfieldvalleyinn.com/mcp/signed-in` instead. It asks you to sign in when it connects.

## Tools

Twelve tools only read and need no sign-in. Ten act for the signed-in guest. Every tool that books, pays or cancels asks you first.

| Tool | What it does | Sign-in |
|---|---|---|
| `list_properties` | The properties | No |
| `get_property` | A property | No |
| `get_location` | Where a property is | No |
| `get_accommodations` | Rooms and beds | No |
| `get_stay_rules` | Stay rules | No |
| `get_policies` | Policies | No |
| `get_breakfast` | Breakfast | No |
| `get_common_questions` | Common questions | No |
| `check_availability` | Check dates | No |
| `find_nearest_dates` | Nearest open dates | No |
| `list_open_dates` | Open dates and prices | No |
| `get_quote` | Get a quote | No |
| `who_am_i` | The signed-in guest | Yes |
| `start_booking` | Start a booking | Yes |
| `list_my_bookings` | My bookings | Yes |
| `get_booking` | Where a booking stands | Yes |
| `cancel_booking` | Cancel a booking | Yes |
| `open_card_payment` | Card payment page | Yes |
| `get_bank_transfer_details` | Bank transfer details | Yes |
| `report_bank_transfer_sent` | Bank transfer sent | Yes |
| `send_request` | Send a request | Yes |
| `get_request` | A request | Yes |

Full tool reference, built from the live server: https://api.deerfieldvalleyinn.com/mcp-tools.md

## Seller, privacy and support

- Seller on every quote: Ozvermont LLC, a Vermont limited liability company.
- Prices are in US dollars.
- We never see or store card numbers: Stripe takes card payments on its own page.
- Privacy policies: https://www.deerfieldvalleyinn.com/privacy and https://www.paradisevermont.com/privacy
- Terms: https://www.deerfieldvalleyinn.com/terms
- Support: info@deerfieldvalleyinn.com

## License

MIT. See [LICENSE](LICENSE). The license covers this repository's files only, not the booking service or the property names and logos.
