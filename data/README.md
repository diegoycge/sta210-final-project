---
editor_options: 
  markdown: 
    wrap: 72
---

# Data used for analysis

Data set source:
<https://data.transportation.gov/Aviation/Consumer-Airfare-Report-Table-1-Top-1-000-Contiguo/4f3n-jbg2/about_data>

For this analysis, we filtered for *2024 Q4* data. The dataset contains
the consumer airfares of the top 1000 contiguous U.S. State City-Pair
markets.

City markets include airports serving the same city markets. For
example, JFK, LGA, and EWR fall under the New York City market, and are
counted in the same category.

The routes listed are non-directional. For instance, New York City - Los
Angeles flights are counted together with Los Angeles - New York City
flights.

The average fares are average prices paid by all fare paying customers.
They include First Class fares for offering carriers, but does not
include free tickets (non-revenue, award tickets, etc.)

## Data Dictionary

`city_1`: consolidate airports serving the same city market; the first
city in non-directional city pair

`city_2`: consolidate airports serving the same city market; the second
city in non-directional city pair

`nsmiles`: non-stop market miles, using radian measure

`passengers`: passengers per day

`fare`: overall average fare. *This is the response variable in this
analysis.*

`carrier_lg`: carrier with the largest market share

`carrier_lg_type`: type of the carrier with the largest market share,
defined by "fullservice", "lcc" (low-cost carrier), and "ulcc
(ultra-low-cost carrier)"

`large_ms`: market share for the carrier with the largest market share

`fare_lg`: average fare for the carrier with the largest market share

`carrier_low`: carrier with the lowest fare

`carrier_lg_type`: type of the carrier with the lowest fare, defined by
"fullservice", "lcc" (low-cost carrier), and "ulcc (ultra-low-cost
carrier)"

`lf_ms`: market share for the carrier with the lowest fare

`fare_low`: average fare for the carrier with the lowest fare

## Carrier Type determination

Broadly, U.S. commercial airlines fall under three categories: full
service/legacy carriers, low-cost carriers, and ultra-low-cost carriers.

Full service carriers are airlines that primarily operate on
hub-and-spoke networks, operate multiple cabin classes (First, Business,
Economy), are in Global airline alliances, have extensive loyalty
programs and operate global widebody fleets. Under this definition, I
have determined United (UA), Delta (DL), American Airlines (AA), Alaska
Airlines (AS), and Hawaii Airlines (HA) as full service carriers, coded
as `fullservice`.

Ultra low cost carriers are airlines that charge very low base fares but
high fees for additional services, such as seat-selection, carry-on
luggage, checked bags, and agent assistance at airport counters. These
carriers tend to operate leisure-heavy routes with high seat density.
Under this definition, I have determined Frontier (F9), Spirit (NK),
Allegiant (G4), Sun Country (SY), and Avelo (XP) as ultra low cost
carriers, coded as `ulcc`.

Low cost carriers operate models in between `ulcc` and `fullservice`.
They offer lower fares than full service carriers, operate simpler fleet
structures, and tends to focus on point-to-point flying instead of
relying on hub transit. These airlines are distinguished from `ulcc` by
their premium offerings (such as JetBlue Mint) and lower additional fees
(such as Southwest charging no baggage fees until May 2025). Under this
definition, I have determined Southwest (WN), JetBlue (B6), and Breeze
(MX) as low cost carriers, coded as `lcc`.
