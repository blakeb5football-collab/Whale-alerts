# HomeIQ

A home maintenance prototype that works like a Carfax for your house. You add your appliances, HomeIQ builds a care plan for each one, reminds you when jobs come due, and logs every finished job into a service record you can share.

Open `index.html` in a browser. There is no build step and nothing to install. Data stays in `localStorage` on the device.

## What's in v1

- **Onboarding in two taps.** Pick a home type, then load a starter plan. You can also start with an empty home.
- **Property.** Set a nickname, home type, year built and an optional address.
- **Inventory.** Add any of 19 preset appliance types with one tap. Each one can have a photo (uses the camera on phones), install date, warranty date (quick 1/2/5/10 yr chips), model and serial. Only the preset is required.
- **Auto care plans.** A built-in schedule for each appliance type. Some jobs repeat on an interval (filters, flushes). Others are tied to a season (gutters in April and November, furnace tune-up in September). Every task is unique per appliance, so plans never duplicate.
- **Today.** Shows what's due now, with one tap to mark it done and an Undo. Also lists the next 30 days and links to the record.
- **Care Atlas.** A 12-month dial. Rings show categories, a needle marks today, and outer bands mark the seasons. Tap a month to list its jobs.
- **Record.** A ledger of completed jobs with an on-time rate. The report can be copied as text or downloaded as HTML.
- **Reminders.** In-app only for now. Tasks due within the lead time you choose, plus warranties ending within 60 days.

Every record can be edited. Completions, removals, skips and photo removals can all be undone.

## Later (not built)

- LLM vision to read model and serial numbers from label photos
- Native push notifications
- Paywall. Free: 1 property and 10 appliances. Paid: $5.99/mo or $49/yr.
