# Practice session booking

This folder holds the Google Apps Script program for the practice session booking system. The booking page is at meredithhatzenbuehler.com/practice.

Status: design approved on 2026-11-13. The build has not started.

## Purpose

Other trainees in Meredith's training book practice sessions with her. The system is custom-built and costs nothing.

## Parts

1. A booking page at `/practice` in this Jekyll site.
2. A Google Apps Script program that runs on Meredith's personal Gmail account. The program reads the calendars, creates events, and sends emails.
3. The Apps Script code lives in this `booking/` folder. Deploy the code with clasp (`clasp push`).
4. `_config.yml` excludes the `booking/` folder, so GitHub Pages does not publish the code.

## Open times

- Meredith adds events to a separate Google calendar named "Availability".
- The program offers only times inside the "Availability" events.
- The program removes times when the main calendar shows that Meredith is busy.

## Booking rules

| Rule | Value |
|---|---|
| Session lengths | 1 hour or 2 hours |
| Start times | Every 30 minutes |
| Break after each booked session | 30 minutes |
| Minimum notice | 18 hours |
| Booking window | 4 weeks ahead |
| Approval | None. A booking is final immediately. |

All values in this table go in one settings file. Change a value in the settings file, not in the code.

## Booking form

- Name (required)
- Email address (required)
- Session length (required)
- Note (optional)

The page gets the trainee's time zone from the browser.

## After a booking

1. The program creates the event on Meredith's main calendar.
2. The program adds a new Google Meet link to the event.
3. The trainee gets a calendar invitation.
4. The trainee gets a confirmation email with a cancel link.
5. Meredith gets a notification.
6. The trainee gets one reminder email 24 hours before the session.

If the booking happened less than 24 hours before the session, the program sends no reminder. Meredith gets no reminder email, because Google Calendar already reminds her of each event.

## Cancel

- Each booking gets a secret cancel link.
- The cancel link deletes the event and emails Meredith.
- There is no cancel deadline.
- To change a time, the trainee cancels and books again.

## Access and spam protection

- The page is unlisted. The page has no menu link and no search engine listing.
- Meredith sends the page address only to trainees.
- The form has a hidden field that only bots fill in.
- The program limits the number of bookings from one email address.

## Email account

The program runs on Meredith's personal Gmail account. The trainees see that address as the sender and as the event organizer.

## Fallback

The current Google Calendar appointment schedule stays live until the custom version works.

## Build steps

1. Build the Apps Script program and the booking page.
2. Install clasp.
3. Create the "Availability" calendar.
4. Deploy the Apps Script program.
5. Test with a booking from a second email address.

## Later: professional service

The professional service gets its own page, separate from `/practice`. Possible additions for that page:

- Reschedule links
- Payments
- A cancel deadline
- A menu link on the site
