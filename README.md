# Check-In-Check-Out

## How it works

Every 3 seconds the following will happen on the mobile Raspberry Pi:

1. Raspberry Pi Takes Picture
2. If QR code was successfully scanned in picture:
    1. The following data is stored on each QR code (JSON Format):
       * Unique ID
       * First Name
       * Last Name
       * Team Role (i.e. programming)
       * Slack Username
    2. If no check ins for the current day for that person or last value in current day was check out:
        1. Sends the following data to the google sheet for the current day under the check in section:
            * Unique ID
            * First Name + Last Name
            * Team Role
            * ISO Timestamp
            * Slack Username
    3. If last value in current day was check in
        1. Sends the following data to the google sheet for the current day under the check out section:
            * Unique ID
            * First Name + Last Name
            * Team Role
            * ISO Timestamp
            * Slack Username

The following happens everyday at midnight on backend application:

1. Creates a new sheet for the current day and formats it

The following happens everyday at 8:00AM on backend application:

1. Backend application gets a list of students that forget to check out and DMs them Slack reminding them that they need to in the future
