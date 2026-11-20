Please save the following as a new skill called "Create events in EventKoi" that is available when working on my WordPress site. My site is set to the timezone ________ {USED_LATER_ON} so that is the center of reference whenever I manually populate an event in the user interface.


# Create events in EventKoi:
The EventKoi plugin stores each event in a custom post type `eventkoi_event`. The event dates and venue do not use the same flat/top-level schema for custom fields as the WP core. The main description also lives in an event field, not the post_content.
## Overall Rules to Follow:
1. If I did not provide a date, time, timezone, or venue in my request, ask me for the missing info before you begin the creation.
2. Keep the post’s status as draft unless I explicitly say to publish it.
3. If I explicitly say to publish it, please always finish your reply by providing the post’s published URL on my site.
4. Never delete an eventkoi_event post. But if I ask you to delete one or "remove it" or "take it down", you can set that post back to draft status and prepend the word "REMOVED:" to its post title.
## Steps to perform for each new event:
1. Create content of type `eventkoi_event` with the given title, `status` = 'draft'.
2. Set these fields: `description`; `date_type` = 'standard'; `standard_type` = 'selected'; `timezone` = {USED_LATER_ON}; `event_days`: one row per day with `start_date` and `end_date` in UTC ISO format and `all_day` = false (NOTE: a two-day long event with hours each day is 1 event with 2 rows); `start_date` = (first day’s start time, in UTC ISO) and `end_date` = (last day’s end, in UTC ISO); `start_timestamp` and `end_timestamp` = (the same moments as Unix timestamps); `locations` has one row with either: `type` = 'physical', `name` = (the venue’s name), `address1` (to be set only if a street address is known), OR WITH `type` = 'online' and `virtual_url` as string; `location` and `address1` matching that row from `locations`; `type` = 'inperson' OR 'virtual' OR 'hybrid'; `virtual_url` to be set only for an event having type 'online' in its `locations`; `recurrence_rules` set empty; `attendance_mode` = 'none' unless I explicitly indicate that RSVPs are wanted. 
3. Assign the new event post to the Default calendar in the `event_cal` taxonomy.
4. Read the new event back to me and tell me each day’s date and time as converted to {USED_LATER_ON}.
