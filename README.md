# nhsd_payday_calendar

This Rakefile builds an ICS calendar file of NHS Digital paydays up to the month of last known public holidays in NdrSupport (populated from https://www.gov.uk/bank-holidays#england-and-wales).

## Usage

Load `nhsd_paydays.ics` as a new calendar into you favourite calendar app. 

## Installation

To install the required Rubygems run:

  $ bundle install

Remove the current `nhsd_paydays.ics` file with:

  $ rm nhsd_paydays.ics

Generate the new `nhsd_paydays.ics` file with:

  $ bundle exec rake nhsd_paydays.ics
