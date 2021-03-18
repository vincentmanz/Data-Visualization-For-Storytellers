week1
================

# COVID-19 data for each US state

## Format the dates

``` r
df <- read_excel("../week1/covid19.xlsx", col_types = c("text", "date", "numeric", "numeric", "numeric", "numeric", "text", "numeric", "numeric"))

#kable(df)
```

## total cases per 100,000 people, and total deaths per 100,000 people

``` r
df_modified <- df %>% 
  mutate(
  case_for_100000 = (df$cases/df$population)*100000,
  death_for_100000 = (df$deaths/df$population)*100000,
)
kable(df_modified)
```

| state                    | date       |   cases | deaths | cases\_new | deaths\_new | state\_postal | state\_fips | population | case\_for\_100000 | death\_for\_100000 |
| :----------------------- | :--------- | ------: | -----: | ---------: | ----------: | :------------ | ----------: | ---------: | ----------------: | -----------------: |
| Alabama                  | 2021-03-17 |  509476 |  10363 |        759 |          26 | AL            |           1 |    4903185 |         10390.715 |         211.352417 |
| Alaska                   | 2021-03-17 |   60451 |    293 |        174 |           1 | AK            |           2 |     731545 |          8263.470 |          40.052218 |
| Arizona                  | 2021-03-17 |  834329 |  16586 |        446 |          12 | AZ            |           4 |    7278717 |         11462.583 |         227.869829 |
| Arkansas                 | 2021-03-17 |  327781 |   5507 |        325 |          14 | AR            |           5 |    3017804 |         10861.574 |         182.483687 |
| California               | 2021-03-17 | 3631245 |  56952 |       3365 |         233 | CA            |           6 |   39512223 |          9190.181 |         144.137676 |
| Colorado                 | 2021-03-17 |  447840 |   6136 |        691 |           7 | CO            |           8 |    5758736 |          7776.707 |         106.551160 |
| Connecticut              | 2021-03-17 |  294328 |   7807 |        373 |           8 | CT            |           9 |    3565287 |          8255.380 |         218.972554 |
| Delaware                 | 2021-03-17 |   91123 |   1516 |        372 |           2 | DE            |          10 |     973764 |          9357.812 |         155.684540 |
| District of Columbia     | 2021-03-17 |   42811 |   1044 |         81 |           2 | DC            |          11 |     705749 |          6066.038 |         147.927946 |
| Florida                  | 2021-03-17 | 1989016 |  32503 |       4599 |          55 | FL            |          12 |   21477737 |          9260.827 |         151.333448 |
| Georgia                  | 2021-03-17 | 1013340 |  17801 |       1979 |          66 | GA            |          13 |   10617423 |          9544.124 |         167.658386 |
| Guam                     | 2021-03-17 |    8745 |    135 |          3 |           0 | GU            |          66 |     159358 |          5487.644 |          84.714919 |
| Hawaii                   | 2021-03-17 |   28423 |    448 |         66 |           0 | HI            |          15 |    1415872 |          2007.455 |          31.641278 |
| Idaho                    | 2021-03-17 |  176589 |   1937 |        456 |           6 | ID            |          16 |    1787065 |          9881.510 |         108.390014 |
| Illinois                 | 2021-03-17 | 1217258 |  23255 |       1513 |          20 | IL            |          17 |   12671821 |          9606.023 |         183.517428 |
| Indiana                  | 2021-03-17 |  677705 |  12893 |        906 |          17 | IN            |          18 |    6732219 |         10066.592 |         191.511892 |
| Iowa                     | 2021-03-17 |  344267 |   5668 |        416 |          10 | IA            |          19 |    3155070 |         10911.549 |         179.647361 |
| Kansas                   | 2021-03-17 |  301763 |   4837 |        593 |           2 | KS            |          20 |    2913314 |         10358.066 |         166.030850 |
| Kentucky                 | 2021-03-17 |  421780 |   5197 |        891 |          31 | KY            |          21 |    4467673 |          9440.709 |         116.324539 |
| Louisiana                | 2021-03-17 |  439002 |   9955 |        445 |          30 | LA            |          22 |    4648794 |          9443.352 |         214.141560 |
| Maine                    | 2021-03-17 |   47591 |    725 |        203 |           0 | ME            |          23 |    1344212 |          3540.439 |          53.934945 |
| Maryland                 | 2021-03-17 |  395817 |   8099 |        917 |          19 | MD            |          24 |    6045680 |          6547.105 |         133.963425 |
| Massachusetts            | 2021-03-17 |  606377 |  16732 |       1711 |          44 | MA            |          25 |    6892503 |          8797.631 |         242.756514 |
| Michigan                 | 2021-03-17 |  680273 |  16800 |       3806 |           4 | MI            |          26 |    9986857 |          6811.683 |         168.221093 |
| Minnesota                | 2021-03-17 |  500030 |   6824 |       1036 |           7 | MN            |          27 |    5639632 |          8866.359 |         121.000803 |
| Mississippi              | 2021-03-17 |  301602 |   6936 |        352 |           7 | MS            |          28 |    2976149 |         10133.968 |         233.052848 |
| Missouri                 | 2021-03-17 |  576363 |   8806 |        795 |           9 | MO            |          29 |    6137428 |          9390.953 |         143.480298 |
| Montana                  | 2021-03-17 |  102602 |   1398 |        133 |           1 | MT            |          30 |    1068778 |          9599.936 |         130.803591 |
| Nebraska                 | 2021-03-17 |  205896 |   2238 |        250 |           0 | NE            |          31 |    1934408 |         10643.877 |         115.694311 |
| Nevada                   | 2021-03-17 |  300190 |   5148 |        303 |          12 | NV            |          32 |    3080156 |          9745.935 |         167.134392 |
| New Hampshire            | 2021-03-17 |   79367 |   1202 |        297 |           0 | NH            |          33 |    1359711 |          5837.049 |          88.401138 |
| New Jersey               | 2021-03-17 |  848875 |  24004 |       4312 |          38 | NJ            |          34 |    8882190 |          9557.046 |         270.248666 |
| New Mexico               | 2021-03-17 |  188907 |   3874 |        243 |          12 | NM            |          35 |    2096829 |          9009.175 |         184.755171 |
| New York                 | 2021-03-17 | 1762032 |  48686 |       6582 |          62 | NY            |          36 |   19453561 |          9057.632 |         250.267804 |
| North Carolina           | 2021-03-17 |  894250 |  11783 |       1687 |          30 | NC            |          37 |   10488084 |          8526.343 |         112.346545 |
| North Dakota             | 2021-03-17 |  101315 |   1490 |        134 |           1 | ND            |          38 |     762062 |         13294.850 |         195.522149 |
| Northern Mariana Islands | 2021-03-17 |     157 |      2 |          3 |           0 | MP            |          69 |      53883 |           291.372 |           3.711746 |
| Ohio                     | 2021-03-17 |  993681 |  17992 |       1458 |           0 | OH            |          39 |   11689100 |          8500.920 |         153.921174 |
| Oklahoma                 | 2021-03-17 |  433516 |   4788 |        491 |           0 | OK            |          40 |    3956971 |         10955.754 |         121.001645 |
| Oregon                   | 2021-03-17 |  160348 |   2358 |        264 |          10 | OR            |          41 |    4217737 |          3801.754 |          55.906758 |
| Pennsylvania             | 2021-03-17 |  979065 |  24749 |       3193 |          35 | PA            |          42 |   12801989 |          7647.757 |         193.321522 |
| Puerto Rico              | 2021-03-17 |  136962 |   2085 |         69 |           2 | PR            |          72 |    3193694 |          4288.514 |          65.284902 |
| Rhode Island             | 2021-03-17 |  132184 |   2588 |        434 |           5 | RI            |          44 |    1059361 |         12477.711 |         244.298214 |
| South Carolina           | 2021-03-17 |  536100 |   8933 |       1231 |          52 | SC            |          45 |    5148714 |         10412.309 |         173.499635 |
| South Dakota             | 2021-03-17 |  114966 |   1915 |        175 |           3 | SD            |          46 |     884659 |         12995.516 |         216.467588 |
| Tennessee                | 2021-03-17 |  781593 |  11555 |       1705 |           8 | TN            |          47 |    6829174 |         11444.913 |         169.200550 |
| Texas                    | 2021-03-17 | 2742767 |  47000 |       4548 |         173 | TX            |          48 |   28995881 |          9459.161 |         162.091988 |
| Utah                     | 2021-03-17 |  379780 |   2037 |        699 |           5 | UT            |          49 |    3205958 |         11846.069 |          63.537950 |
| Vermont                  | 2021-03-17 |   17106 |    217 |         59 |           2 | VT            |          50 |     623989 |          2741.394 |          34.776254 |
| Virgin Islands           | 2021-03-17 |    2767 |     25 |          0 |           0 | VI            |          78 |     106405 |          2600.442 |          23.495137 |
| Virginia                 | 2021-03-17 |  598468 |  10154 |       1327 |          50 | VA            |          51 |    8535519 |          7011.501 |         118.961718 |
| Washington               | 2021-03-17 |  354774 |   5212 |        845 |           6 | WA            |          53 |    7614893 |          4658.949 |          68.444823 |
| West Virginia            | 2021-03-17 |  136334 |   2565 |        315 |          19 | WV            |          54 |    1792147 |          7607.300 |         143.124420 |
| Wisconsin                | 2021-03-17 |  627266 |   7203 |        729 |          19 | WI            |          55 |    5822434 |         10773.261 |         123.711149 |
| Wyoming                  | 2021-03-17 |   55449 |    693 |         97 |           0 | WY            |          56 |     578759 |          9580.672 |         119.738959 |

## visualization

``` r
# remove Northern Mariana Islands
df_modified<- df_modified[- grep("Mariana", df_modified$state),]
df_modified <- df_modified %>% 
  mutate(across(where(is.numeric), ~ round(., digits = 0)))
```

``` r
df_modified <- df_modified %>% 
  mutate(across(where(is.numeric), ~ round(., digits = 0)))

#scale the bubble sizes

my_scale <- function(x){
  scales::rescale(x, to = c(5, 90))
}

Plot with echarts4r
df_modified %>%
  e_charts(case_for_100000) %>%
  e_scatter(death_for_100000,
            population,
            scale = my_scale,
            bind = state) %>%
  e_legend(FALSE)  %>%
  e_mark_line(
    lineStyle = list(color = "#E10056"),
    data = list(type = "average"),
    title = "US\ndeath rate\naverage",
    silent = TRUE
  ) %>%
  e_mark_area(
    "death_for_100000",
    data = list(list(xAxis = 0, yAxis = 143),
                list(xAxis = 15000, yAxis = 300)),
    itemStyle = list(color = "#E10056",  opacity = 0.3),
    silent = TRUE
  ) %>%
  e_mark_point("death_for_100000",silent = TRUE, 
               data = list(x="200", 
                           y="220", 
                           itemStyle = list(color = "transparent"),
                           value="Over the National average")) %>%
  e_title("Where the COVID-19 is more deadly?",
          "Death and case rate for 100,000 inhabitants.\nSource: www.buzzfeed.com\nLast accessed:17-03-2021\nAuthor: Vincent Manzanila") %>%
  e_tooltip(formatter = htmlwidgets::JS("
      function(params){return('<strong>' + params.name + 
                '</strong><br />death rate: ' + params.value[1]+ 
                '</strong><br />case rate: ' + params.value[0])}")) %>%
  e_animation(duration = 5000) %>%
  e_theme("chalk") %>% 
  e_datazoom(x_index = 0, type = "slider") %>% 
  e_datazoom(y_index = 0, type = "slider") %>%
  e_toolbox_feature(feature = "saveAsImage") %>%
  e_grid(top = 100)
```

<center>

![COVID](https://github.com/vincentmanz/Data-Visualization-For-Storytellers/blob/master/week2/COVID-per-state.gif)

</center>
