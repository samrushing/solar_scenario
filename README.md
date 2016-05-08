# solar_scenario
Python program to compute different scenarios for solar power.

This is a program I use to simulate different scenarios for installing
residential solar power.  To use this program you'll need to get some
data from http://pvwatts.nrel.gov/ for your particular house.  There
you can draw a solar panel on your roof, and their calculations will
give you a reliable estimate for the solar output of a system of that
size.  In the final page of their output is an option to download
monthly data: this is the file you will need as input for this script.

The python script then scales that scenario (linearly) and calculates
your return on investment over a span of years (defaulting to 15
years).

This program does not take into account any federal or state kickback
programs, though you can estimate their effects by adjusting the
```cpw``` (cost per watt) argument.

# sample output

This example runs a 15-year simulation with a Cost Per Watt of $4 and a
Return On Investment of 7%::

```
$ python solar.py
usage: solar.py [-h] [--roi ROI] [--years YEARS] [--nem NEM] [--cpw CPW]
                [--rate-rise RATE_RISE] [--base BASE] --pvwatts PVWATTS
solar.py: error: argument --pvwatts is required
$ python solar.py --pvwatts ~/Downloads/pvwatts_monthly.csv --cpw 4 --roi 7
yr        none      10.0kW       7.5kW       5.0kW       4.0kW       3.0kW       2.0kW
 1     103672 +     64066 -     74407 -     84477 -     88412 -     92278 -     96096 -
 2     107378 +     68401 -     79086 -     89192 -     93034 -     96729 -    100321 -
 3     111105 +     73022 -     84055 -     94156 -     97874 -    101358 -    104674 -
 4     114840 +     77948 -     89332 -     99382 -    102941 -    106167 -    109153 -
 5     118565 +     83199 -     94935 -    104882 -    108244 -    111159 -    113755 -
 6     122262 +     88797 -    100885 -    110669 -    113790 -    116338 -    118476 -
 7     125909 +     94765 -    107201 -    116757 -    119588 -    121704 -    123310 -
 8     129482 +    101127 -    113908 -    123159 -    125648 -    127260 -    128250 -
 9     132955 +    107909 -    121028 -    129890 -    131976 -    133007 +    133289 +
10     136296 +    115139 -    128588 -    136965 +    138582 +    138943 +    138416 +
11     139471 +    122846 -    136612 -    144401 +    145474 +    145070 +    143621 +
12     142442 +    131062 -    145131 +    152212 +    152660 +    151384 +    148890 +
13     145166 +    139820 -    154174 +    160416 +    160149 +    157883 +    154208 +
14     147594 +    149157 +    163772 +    169030 +    167947 +    164562 +    159555 +
15     149675 +    159109 +    173960 +    178071 +    176063 +    171415 +    164912 +
```

