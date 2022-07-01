# income

> If you look at something like
> https://www.bls.gov/oes/current/oes_nat.htm you'd think doctors are
> the highest-paying jobs, but then https://www.levels.fyi/... The
> whole distribution matters. If you're a student or career-changer,
> how do you optimize?

https://twitter.com/planarrowspace/status/1533092123142238215


 * [PUMS 2019 1-year data][]
     * There are CSV and "Unix" (really sas7bdat) formats.
     * There are "h" (housing unit) and "p" (person) record files.
     * There's a file per state.
     * So: "csv_hwv.zip" is the CSV format housing unit data file for
       West Virginia.
 * [PUMS 2019 data dictionary][]

[PUMS 2019 1-year data]: https://www2.census.gov/programs-surveys/acs/data/pums/2019/1-Year/
[PUMS 2019 data dictionary]: https://www2.census.gov/programs-surveys/acs/tech_docs/pums/data_dict/PUMS_Data_Dictionary_2019.pdf


"""
PERSON RECORD

PERSON RECORD-BASIC VARIABLES

RT Character 1
Record Type
H .Housing Record or Group Quarters Unit
P .Person Record

ADJINC Character 7
Adjustment factor for income and earnings dollar amounts (6 implied
decimal places)
1010145 .2019 factor (1.010145)


PERSON RECORD-PERSON VARIABLES

AGEP Numeric 2
Age
0 .Under 1 year
1..99 .1 to 99 years (Top-coded)

OCCP Character 4
Occupation recode for 2018 and later based on 2018 OCC codes
# long long list

PINCP Numeric 7
Total person's income (signed, use ADJINC to adjust to constant
dollars)
bbbbbbb .N/A (less than 15 years old)
0 .None
-19998 .Loss of $19998 or more (Rounded and bottom-
.coded components)
-19997..-1 .Loss $1 to $19997 (Rounded components)
1..4209995 .$1 to $4209995 (Rounded and top-coded
.components)
"""


---

Downloading data...

```bash
mkdir data
cd data
# Looks like you can get state files or this big US file...
wget https://www2.census.gov/programs-surveys/acs/data/pums/2019/1-Year/csv_pus.zip
unzip csv_pus.zip
rm csv_pus.zip
chmod a-x *
```
