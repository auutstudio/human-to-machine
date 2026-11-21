---
type: "skill"
for: {"topic": "events", "app": [{"name": "EventKoi plugin", "url": "https://eventkoi.com/"}]} 
original: "https://eventkoi.com/blog/add-events-to-wordpress-with-chatgpt-or-claude/" 
---

Please save the following as a new skill called "Create events in EventKoi" that is available when working on my WordPress site. My site is set to the following timezone: ________, so that became the center of reference when I manually populate an event in the user interface.


# Create events in EventKoi:
The EventKoi plugin stores each event in a custom post type `eventkoi_event`. The event dates and venue do not use the same flat/top-level schema for custom fields as the WP Core. Likewise, the main description is stored in an event field, not the `post_content`.
When you save this skill the first time, explictly declare the following variable to equal the TZ database name (IANA reference) for the timezone I mentioned above.
`MY_SITE_TIMEZONE = ''`
## Overall Rules to Follow:
1. If I did not provide a date, time, or venue in my request, ask me for the missing info before you begin the creation. If I mention a city that is not located in MY_SITE_TIMEZONE, then ask me to clarify if the start time refers to that city’s local time.
2. Keep the post’s status as draft unless I explicitly say to publish it.
3. If I explicitly say to publish it, please always finish your reply by providing the post’s published URL on my site.
4. Never delete an eventkoi_event post. But if I ask you to delete one or "remove it" or "take it down", you can set that post back to draft status and prepend the word "REMOVED:" to its post title.
## Steps to perform for each new event:
1. Create content of type `eventkoi_event` with the given title, `status` = 'draft'.
2. Set these fields: `description`; `date_type` = 'standard'; `standard_type` = 'selected'; `timezone` = MY_SITE_TIMEZONE; `event_days`: one row per day with `start_date` and `end_date` in UTC ISO format and `all_day` = false (NOTE: a two-day long event with hours each day is 1 event with 2 rows); `start_date` = (first day’s start time, in UTC ISO) and `end_date` = (last day’s end, in UTC ISO); `start_timestamp` and `end_timestamp` = (the same moments as Unix timestamps); `locations` has one row with either: `type` = 'physical', `name` = (the venue’s name), `address1` (to be set only if a street address is known), OR WITH: `type` = 'online' and `virtual_url` (as string); a separate field for `location` and `address1` each set to match those values from the row just mentioned; `type` = 'inperson' OR 'virtual' OR 'hybrid'; `virtual_url` (to be set only when an event has type 'online' in its `locations`); `recurrence_rules` (set empty); `attendance_mode` = 'none' unless I explicitly indicate that RSVPs are wanted. 
3. Assign the new event post to the Default calendar in the `event_cal` taxonomy.
4. Read the new event back to me and tell me each day’s date and time as converted to MY_SITE_TIMEZONE.
