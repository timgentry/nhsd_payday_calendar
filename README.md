# nhsd_payday_calendar

This Rakefile builds an ICS calendar file of NHS Digital paydays up to the month of last known public holidays in NdrSupport (populated from https://www.gov.uk/bank-holidays#england-and-wales).

This calendar is supplied as-is, I cannot make any guarantee that these calculated dates are 100% correct.

## Usage

Load `nhsd_paydays.ics` as a new calendar into you favourite calendar app or subscribe to it at https://raw.githubusercontent.com/timgentry/nhsd_payday_calendar/main/nhsd_paydays.ics with very infrequent refreshes (e.g. once a week).

## Installation

To install the required Rubygems run:

    $ bundle install

Remove the current `nhsd_paydays.ics` file with:

    $ rm nhsd_paydays.ics

Generate the new `nhsd_paydays.ics` file with:

    $ bundle exec rake nhsd_paydays.ics
