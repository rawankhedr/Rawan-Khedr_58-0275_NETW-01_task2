Task 2

RawanKhedr
58-0275
Networks


I read 283 lines. 24 were quarantined. 4 malformed student.id, 4 had total differring from the sum of qty × price, 3 with qty below 1, 3 with an unknown ticket type, 3 booked on or after the event date, 2 with no event, 2 with no tickets and 3 as duplicate booking_id. 259 bookings (314 ticket rows) left. The duplicate check runs after validation because keeping the first copy only makes sense among valid copies. If the first copy is broken and a later one is fine, checking duplicates first would discard the good one! On this file the counts happen to be identical in both orders because every resent booking is an exact copy of a valid original. The drifting field is promo_code. it first appears on 2026-10-20 at 01:05 UTC (booking B0125) and is in 173 of the 259 valid bookings. It is optional in the contract so a booking without it stays valid and gets a NULL in that column of bookings. total is not a column of fact_ticket_sales because it belongs to the whole booking, while the fact has one row per ticket entry. A booking with several ticket types would repeat its total on each row, so SUM(total) over the fact gives 42,000 EGP instead of the true 31,285 EGP (which is what SUM(amount) returns.)

Files

- task2.ipynb: the whole pipeline (run top to bottom; reads everything from DATA)
- bookings.jsonl: the input, unchanged
- quarantine.jsonl: rejected bookings with booking_id, reason, all reasons, line number and the raw document
- star: dim_event.parquet, dim_student.parquet, and fact_ticket_sales/booked_month=YYYY-MM/
- requirements.txt: package versions
