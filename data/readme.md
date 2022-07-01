# data

 * `codes.csv` was built by hand from the
   [PUMS 2019 data dictionary][]
 * `categories.csv` was built by hand from the
   [2018 Census Occupation Code List][]
 * `data.csv` was built as shown below

[PUMS 2019 data dictionary]: https://www2.census.gov/programs-surveys/acs/tech_docs/pums/data_dict/PUMS_Data_Dictionary_2019.pdf
[2018 Census Occupation Code List]: https://www2.census.gov/programs-surveys/demo/guidance/industry-occupation/2018-occupation-code-list-and-crosswalk.xlsx


### `data.csv`

```bash
# Looks like you can get state files or this big US file...
wget https://www2.census.gov/programs-surveys/acs/data/pums/2019/1-Year/csv_pus.zip
unzip csv_pus.zip
rm csv_pus.zip
chmod a-x *
head -1 psam_pusa.csv | sed 's/,/\n/g' | cat -n
# AGEP is 10, OCCP is 102, PINCP is 105
cat psam_pusa.csv | cut -d, -f10,102,105 > data.csv
tail -n +2 psam_pusb.csv | cut -d, -f10,102,105 >> data.csv
# That gets the data down to 34M
```
