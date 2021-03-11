week1
================

# GDP per country

``` r
df <- read.csv("week1/gdp_pc_2018.csv")
glimpse(df)
```

    ## Rows: 217
    ## Columns: 3
    ## $ country <chr> "Andorra", "United Arab Emirates", "Afghanistan", "Antigua an…
    ## $ gdp_pc  <dbl> NA, 68548.5147, 2241.9232, 21614.0661, 13833.9816, 13014.9920…
    ## $ iso3c   <chr> "AND", "ARE", "AFG", "ATG", "ALB", "ARM", "AGO", "ARG", "ASM"…

``` r
# median, mean
gdp_stats <- df %>% summarise(mean = mean(gdp_pc,na.rm = TRUE), 
                              median = median(gdp_pc,na.rm = TRUE), 
                              n = n())
kable(gdp_stats)
```

|     mean |   median |   n |
| -------: | -------: | --: |
| 21835.79 | 13833.98 | 217 |

``` r
q <-  as.data.frame(quantile(df$gdp_pc, na.rm = TRUE, c(0.2, 0.4, 0.6, 0.8)))
colnames(q) <- c("quantiles values")
kable(q)
```

|     | quantiles values |
| :-- | ---------------: |
| 20% |         4017.139 |
| 40% |        10932.866 |
| 60% |        18113.818 |
| 80% |        37314.517 |

``` r
library(scales)
```

    ## 
    ## Attaching package: 'scales'

    ## The following object is masked from 'package:viridis':
    ## 
    ##     viridis_pal

``` r
df %>% ggplot(aes(x = gdp_pc, fill="country\ncount")) +
  geom_histogram(
    color = "#e9ecef",
    binwidth = 5000,
    na.rm = TRUE,
    breaks = seq(0, 140000, by=5000)
  ) +
  scale_fill_viridis(discrete = TRUE) +
  scale_color_viridis(discrete = TRUE) +
  theme_ipsum() +
  labs(title = "GDP per country") +
  ylab("Number of nations") +
  xlab("GDP") +
  scale_x_continuous(labels = comma, breaks = seq(0, 140000, by=5000),limits = c(0,140000)) +
  theme(axis.text.x =element_text(angle=90,size = 11),
        axis.text.y =element_text(size = 11),
        legend.title=element_blank()) 
```

![](README_files/figure-gfm/histogram-1.png)<!-- -->

# COVID-19 data for each US state

``` r
library(readxl)
df <- read_excel("~/covid19.xlsx", col_types = c("text", "date", "numeric", "numeric", "numeric", "numeric", "text", "numeric", "numeric"))
```

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B2 / R2C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B3 / R3C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B4 / R4C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B5 / R5C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B6 / R6C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B7 / R7C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B8 / R8C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B9 / R9C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B10 / R10C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B11 / R11C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B12 / R12C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B13 / R13C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B14 / R14C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B15 / R15C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B16 / R16C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B17 / R17C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B18 / R18C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B19 / R19C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B20 / R20C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B21 / R21C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B22 / R22C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B23 / R23C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B24 / R24C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B25 / R25C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B26 / R26C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B27 / R27C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B28 / R28C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B29 / R29C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B30 / R30C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B31 / R31C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B32 / R32C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B33 / R33C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B34 / R34C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B35 / R35C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B36 / R36C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B37 / R37C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B38 / R38C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B39 / R39C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B40 / R40C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B41 / R41C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B42 / R42C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B43 / R43C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B44 / R44C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B45 / R45C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B46 / R46C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B47 / R47C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B48 / R48C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B49 / R49C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B50 / R50C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B51 / R51C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B52 / R52C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B53 / R53C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B54 / R54C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B55 / R55C2

    ## Warning in read_fun(path = enc2native(normalizePath(path)), sheet_i = sheet, :
    ## Coercing numeric to date B56 / R56C2

``` r
kable(glimpse(df))
```

    ## Rows: 55
    ## Columns: 9
    ## $ state        <chr> "Alabama", "Alaska", "Arizona", "Arkansas", "California"…
    ## $ date         <dttm> 2021-03-10, 2021-03-10, 2021-03-10, 2021-03-10, 2021-03…
    ## $ cases        <dbl> 501398, 59451, 828630, 325700, 3611008, 441611, 288657, …
    ## $ deaths       <dbl> 10222, 291, 16404, 5382, 54877, 6092, 7752, 1492, 1037, …
    ## $ cases_new    <dbl> 782, 152, 830, 317, 3464, 1132, 512, 212, 96, 4853, 1840…
    ## $ deaths_new   <dbl> 36, 0, 78, 25, 257, 8, 13, 10, 1, 59, 73, 0, 3, 9, 28, 1…
    ## $ state_postal <chr> "AL", "AK", "AZ", "AR", "CA", "CO", "CT", "DE", "DC", "F…
    ## $ state_fips   <dbl> 1, 2, 4, 5, 6, 8, 9, 10, 11, 12, 13, 66, 15, 16, 17, 18,…
    ## $ population   <dbl> 4903185, 731545, 7278717, 3017804, 39512223, 5758736, 35…

| state                    | date       |   cases | deaths | cases\_new | deaths\_new | state\_postal | state\_fips | population |
| :----------------------- | :--------- | ------: | -----: | ---------: | ----------: | :------------ | ----------: | ---------: |
| Alabama                  | 2021-03-10 |  501398 |  10222 |        782 |          36 | AL            |           1 |    4903185 |
| Alaska                   | 2021-03-10 |   59451 |    291 |        152 |           0 | AK            |           2 |     731545 |
| Arizona                  | 2021-03-10 |  828630 |  16404 |        830 |          78 | AZ            |           4 |    7278717 |
| Arkansas                 | 2021-03-10 |  325700 |   5382 |        317 |          25 | AR            |           5 |    3017804 |
| California               | 2021-03-10 | 3611008 |  54877 |       3464 |         257 | CA            |           6 |   39512223 |
| Colorado                 | 2021-03-10 |  441611 |   6092 |       1132 |           8 | CO            |           8 |    5758736 |
| Connecticut              | 2021-03-10 |  288657 |   7752 |        512 |          13 | CT            |           9 |    3565287 |
| Delaware                 | 2021-03-10 |   88891 |   1492 |        212 |          10 | DE            |          10 |     973764 |
| District of Columbia     | 2021-03-10 |   42006 |   1037 |         96 |           1 | DC            |          11 |     705749 |
| Florida                  | 2021-03-10 | 1957578 |  31947 |       4853 |          59 | FL            |          12 |   21477737 |
| Georgia                  | 2021-03-10 | 1003181 |  17491 |       1840 |          73 | GA            |          13 |   10617423 |
| Guam                     | 2021-03-10 |    8725 |    134 |          4 |           0 | GU            |          66 |     159358 |
| Hawaii                   | 2021-03-10 |   27944 |    445 |         41 |           3 | HI            |          15 |    1415872 |
| Idaho                    | 2021-03-10 |  174381 |   1903 |        459 |           9 | ID            |          16 |    1787065 |
| Illinois                 | 2021-03-10 | 1206362 |  23067 |       1669 |          28 | IL            |          17 |   12671821 |
| Indiana                  | 2021-03-10 |  672439 |  12775 |        869 |          13 | IN            |          18 |    6732219 |
| Iowa                     | 2021-03-10 |  341378 |   5602 |        487 |          27 | IA            |          19 |    3155070 |
| Kansas                   | 2021-03-10 |  300261 |   4851 |        738 |          35 | KS            |          20 |    2913314 |
| Kentucky                 | 2021-03-10 |  416402 |   5026 |       1009 |          25 | KY            |          21 |    4467673 |
| Louisiana                | 2021-03-10 |  435514 |   9812 |        588 |          43 | LA            |          22 |    4648794 |
| Maine                    | 2021-03-10 |   46254 |    723 |        195 |           0 | ME            |          23 |    1344212 |
| Maryland                 | 2021-03-10 |  389748 |   8002 |        900 |          14 | MD            |          24 |    6045680 |
| Massachusetts            | 2021-03-10 |  595264 |  16509 |       1657 |          53 | MA            |          25 |    6892503 |
| Michigan                 | 2021-03-10 |  662553 |  16690 |       2652 |           7 | MI            |          26 |    9986857 |
| Minnesota                | 2021-03-10 |  493081 |   6773 |        905 |           9 | MN            |          27 |    5639632 |
| Mississippi              | 2021-03-10 |  298445 |   6845 |        437 |          11 | MS            |          28 |    2976149 |
| Missouri                 | 2021-03-10 |  572148 |   8728 |        716 |          13 | MO            |          29 |    6137428 |
| Montana                  | 2021-03-10 |  101374 |   1388 |        145 |           2 | MT            |          30 |    1068778 |
| Nebraska                 | 2021-03-10 |  204144 |   2231 |        338 |          10 | NE            |          31 |    1934408 |
| Nevada                   | 2021-03-10 |  297216 |   5069 |        331 |          15 | NV            |          32 |    3080156 |
| New Hampshire            | 2021-03-10 |   77463 |   1187 |        211 |           2 | NH            |          33 |    1359711 |
| New Jersey               | 2021-03-10 |  822817 |  23691 |       3775 |          56 | NJ            |          34 |    8882190 |
| New Mexico               | 2021-03-10 |  187487 |   3841 |        249 |           9 | NM            |          35 |    2096829 |
| New York                 | 2021-03-10 | 1713287 |  48092 |       6106 |          92 | NY            |          36 |   19453561 |
| North Carolina           | 2021-03-10 |  882489 |  11628 |       1904 |          51 | NC            |          37 |   10488084 |
| North Dakota             | 2021-03-10 |  100645 |   1481 |        101 |           2 | ND            |          38 |     762062 |
| Northern Mariana Islands | 2021-03-10 |     146 |      2 |          0 |           0 | MP            |          69 |      53883 |
| Ohio                     | 2021-03-10 |  983487 |  17662 |       1868 |           0 | OH            |          39 |   11689100 |
| Oklahoma                 | 2021-03-10 |  430250 |   4701 |        818 |           0 | OK            |          40 |    3956971 |
| Oregon                   | 2021-03-10 |  158360 |   2314 |        331 |           5 | OR            |          41 |    4217737 |
| Pennsylvania             | 2021-03-10 |  960877 |  24485 |       2611 |          40 | PA            |          42 |   12801989 |
| Puerto Rico              | 2021-03-10 |  135666 |   2071 |        114 |           4 | PR            |          72 |    3193694 |
| Rhode Island             | 2021-03-10 |  129595 |   2559 |        318 |           3 | RI            |          44 |    1059361 |
| South Carolina           | 2021-03-10 |  528473 |   8781 |       1125 |          18 | SC            |          45 |    5148714 |
| South Dakota             | 2021-03-10 |  113962 |   1904 |        209 |           3 | SD            |          46 |     884659 |
| Tennessee                | 2021-03-10 |  772634 |  11506 |       1342 |          17 | TN            |          47 |    6829174 |
| Texas                    | 2021-03-10 | 2710622 |  45956 |       5350 |         202 | TX            |          48 |   28995881 |
| Utah                     | 2021-03-10 |  376327 |   1992 |        691 |           2 | UT            |          49 |    3205958 |
| Vermont                  | 2021-03-10 |   16371 |    211 |         85 |           0 | VT            |          50 |     623989 |
| Virgin Islands           | 2021-03-10 |    2755 |     25 |         11 |           0 | VI            |          78 |     106405 |
| Virginia                 | 2021-03-10 |  589375 |   9849 |       1246 |          59 | VA            |          51 |    8535519 |
| Washington               | 2021-03-10 |  349881 |   5159 |        685 |          18 | WA            |          53 |    7614893 |
| West Virginia            | 2021-03-10 |  134158 |   2330 |        302 |           4 | WV            |          54 |    1792147 |
| Wisconsin                | 2021-03-10 |  623150 |   7151 |        706 |          13 | WI            |          55 |    5822434 |
| Wyoming                  | 2021-03-10 |   55014 |    691 |         42 |           0 | WY            |          56 |     578759 |
