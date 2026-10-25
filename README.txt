Catering Money Manager V19.5.16 — Sync Verification & Navigation Polish

This release refreshes the responsive dashboard and adds a mobile bottom navigation bar and quick actions. Existing data, booking, season, payment, expense, partner, backup, and cloud-sync logic are retained.

Install by replacing the app files in your existing GitHub repository. Do not delete your Supabase project or clear browser website data. Keep a backup before updating.

Catering Money Manager V19.5.9 — Separate Bookings Menu & Bug Review

What changed:
1. Added a separate Bookings menu for upcoming party bookings and sent orders, with date/status/search filters.
2. Added per-booking WhatsApp sharing and sharing of the visible worker schedule. Worker messages include party date, customer/contact, service type, menu/items, member count, order status, and notes; they omit payment amounts.
3. Kept the existing Catering, Money Received, Expenses, Partners, seasons, multiple-advance, and cloud-sync workflows.
4. Fixed Expenses history to follow its selected season and Transfers history to follow its own selected season dropdown rather than always showing only the active season.
5. Updated the service-worker cache name to V19.5.9 so older cache keys are retired during activation.
6. The booking date label now changes between “Party / booking date” for unsent bookings and “Date food sent” for sent orders.

Previously encountered issues considered:
- Money Received catering selection unexpectedly changing during refresh/save.
- Expense edit not retaining the selected “Spent by” partner.
- Selection dropdowns resetting during rerender.
- Calendar navigation, Today, date selection, and dd/mm/yyyy vs ISO conversion.
- Advance before sending order, optional order total for an early booking, multiple advances with separate receiving partners/payment modes, and preventing duplicate transfer when marking an order sent.
- Earlier blank/sign-in concerns: the current app's cloud sign-in UI is in Dashboard; this package does not change the Supabase project, credentials, schema, or auth configuration.

Validation:
- JavaScript syntax check and ZIP integrity check should be run on this package.
- Static DOM reference and functional-flow checks are included in the build review; this does not substitute for testing with the user's live Supabase project and existing records.

Install safely:
- Back up data before replacing files.
- Keep existing cloud-config.js and Supabase project/data.
- Do not rerun supabase-setup.sql and do not clear browser data.
- After deployment, test the Bookings menu, WhatsApp sharing, selected season in Expenses, calendar, and a draft booking with multiple advances before using it for live payments.

V19.5.11 fix: New Booking referenced updateOrderStatusLabel(), which was not defined in the inline application script. The action now updates the date label directly and opens the catering form. Cache version bumped.


V19.5.16 additions:
- Verify Data compares this device against the signed-in cloud snapshot without changing records. Differences produce a warning and are not auto-overwritten.
- Bottom navigation has clearer active state, touch feedback, keyboard focus styling, and reduced-motion support.
- Verification compares saved records and the active-season reference; it does not prove another device has no unsynced local changes.
