# Assessment Notes

## Summary

Fixed three high-value bugs found through manual testing:

1. Status filter: The SQL WHERE clause had incorrect AND/OR grouping, so status filtering was not consistently applied. Added parentheses around the title/description search conditions.

2. Pagination after filtering: Changing search or status while on a later page could show “No tasks found” even when matching tasks existed. Reset the page to 1 whenever search or status changes.

3. Artificial API delay: The task API intentionally slept based on search length, adding about 700 ms to requests such as "api". Removed the artificial delay and related complexity logging.

## What I Did Not Change

I did not modify the Java runtime/upgrade files, task model, status enum, API request helper, or pagination implementation because they were functioning correctly during testing.

## Biggest Remaining Risk

The application has limited automated test coverage. The fixes were verified manually through the UI and browser Network tab, but additional automated tests would reduce regression risk.

## AI / Tools Used

Used AI assistance to understand the code, identify likely root causes, and plan/debug fixes. Verified each fix manually by reproducing the original behavior and testing the corrected behavior.