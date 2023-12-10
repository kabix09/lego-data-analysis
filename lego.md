---
title: "Lego Rebbrickable Data Analysis"
author: "Jakub Fiturski"
date: "2023-12-10"
output:
  html_document: 
    self_contained: yes
    keep_md: yes
    toc: yes
    toc_float: yes
    theme: spacelab
    number_sections: yes
    df_print: kable
---





# Problem

Raport służy do analizy zmian różnorodności możliwych do zbudowania zestawów LEGO na przestrzeni ostatnich 80 lat.

## Źródło danych

Do analizy wykorzystano zbiór danych udostępniony przez prowadzącego na podstawie danych z [Rebrickable](https://rebrickable.com/) - platformy do dzielenia się, przeglądania i zarządzania swoimi zestawami klocków LEGO. Zbiór zawiera informacje o oficjalnych i MOC'owych zestawach LEGO oraz tworzących go częściach.

## Zbiór danych

Zbiór składa się z 12 plików SCV powiązanych ze sobą w następujacy sposób.

Na potrzeby analizy zostały one połączone w trzy niezależne dataframy przedstawione w kolejnych sekcjach.

![](./data/rebrickable/rebrickable_schema_v3.PNG)



### Zestawy




|set_num |name                       | year| num_parts|theme        |theme_parent |
|:-------|:--------------------------|----:|---------:|:------------|:------------|
|001-1   |Gears                      | 1965|        43|NA           |NA           |
|0011-2  |Town Mini-Figures          | 1979|        12|Classic Town |Town         |
|0011-3  |Castle 2 for 1 Bonus Offer | 1987|         0|Lion Knights |Castle       |
|0012-1  |Space Mini-Figures         | 1979|        12|Supplemental |Space        |
|0013-1  |Space Mini-Figures         | 1979|        12|Supplemental |Space        |
|0014-1  |Space Mini-Figures         | 1979|         2|Supplemental |Space        |

### Minifigurki w zestawach


|name                                                                         |fig_num    | num_parts| quantity|inv_set_num |
|:----------------------------------------------------------------------------|:----------|---------:|--------:|:-----------|
|Emma - Lavender Top, Magenta Skirt                                           |fig-001549 |         4|        1|3931-1      |
|Danny Longlegs / Corporal Steel                                              |fig-000764 |         4|        1|6942-1      |
|Coca-Cola Defender 2                                                         |fig-000555 |         4|        1|4444-1      |
|Minnie Mouse with Dark Pink with White Spots Dress and Bow (CMF)             |fig-000574 |         5|        1|71012-11    |
|Coast Guard, Blue Jacket with Zipper and ID Badge, Blue Cap, Blue Sunglasses |fig-000842 |         4|        1|6435-1      |
|Coast Guard, Woman, Blue Jacket with Zipper and ID Badge. Black Hair         |fig-008641 |         4|        1|6435-1      |

### Części w zestawach





|part_num       |part_name               |category_name                                                   |part_material | is_spare|color_name           |color_rgb | color_is_trans| quantity|inv_set_num |
|:--------------|:-----------------------|:---------------------------------------------------------------|:-------------|--------:|:--------------------|:---------|--------------:|--------:|:-----------|
|48379c01       |Large Buildable Figures |Large Figure Torso and Legs, Promo Figure Base with Feet        |Plastic       |        0|Dark Bluish Gray     |6C6E68    |              1|        1|7922-1      |
|48395          |Minifig Accessories     |Sports Snowboard from McDonald's Promotional Set                |Plastic       |        0|Light Gray           |9BA19D    |              1|        1|7922-1      |
|stickerupn0077 |Stickers                |Sticker Sheet for Set 7922-1                                    |Plastic       |        0|[No Color/Any Color] |05131D    |              1|        1|7922-1      |
|upn0342        |Minifig Accessories     |Sports Promo Paddle from McDonald's Sports Sets                 |Plastic       |        0|Black                |05131D    |              1|        1|7922-1      |
|upn0350        |Minifigs                |Sports Promo Figure Head Torso Assembly McDonald's Set 6 (7922) |Plastic       |        0|Orange               |FE8A18    |              1|        1|7922-1      |
|2343           |Minifig Accessories     |Equipment Goblet / Glass                                        |Plastic       |        0|Trans-Clear          |FCFCFC    |              0|        1|3931-1      |


## Podsumowanie danych

### Zestawy


|   |  set_num        |    name         |     year    |  num_parts     |   theme         |theme_parent     |
|:--|:----------------|:----------------|:------------|:---------------|:----------------|:----------------|
|   |Length:23501     |Length:23501     |Min.   :1949 |Min.   :    0.0 |Length:23501     |Length:23501     |
|   |Class :character |Class :character |1st Qu.:2000 |1st Qu.:    3.0 |Class :character |Class :character |
|   |Mode  :character |Mode  :character |Median :2012 |Median :   33.0 |Mode  :character |Mode  :character |
|   |NA               |NA               |Mean   :2006 |Mean   :  167.4 |NA               |NA               |
|   |NA               |NA               |3rd Qu.:2018 |3rd Qu.:  144.0 |NA               |NA               |
|   |NA               |NA               |Max.   :2024 |Max.   :11695.0 |NA               |NA               |

### Minifigurki


|   |    name         |  fig_num        |  num_parts     |   quantity     |inv_set_num      |
|:--|:----------------|:----------------|:---------------|:---------------|:----------------|
|   |Length:20858     |Length:20858     |Min.   :  0.000 |Min.   :  1.000 |Length:20858     |
|   |Class :character |Class :character |1st Qu.:  4.000 |1st Qu.:  1.000 |Class :character |
|   |Mode  :character |Mode  :character |Median :  4.000 |Median :  1.000 |Mode  :character |
|   |NA               |NA               |Mean   :  4.813 |Mean   :  1.062 |NA               |
|   |NA               |NA               |3rd Qu.:  5.000 |3rd Qu.:  1.000 |NA               |
|   |NA               |NA               |Max.   :143.000 |Max.   :100.000 |NA               |

### Klocki


|   |  part_num       | part_name       |category_name    |part_material    |   is_spare     | color_name      | color_rgb       |
|:--|:----------------|:----------------|:----------------|:----------------|:---------------|:----------------|:----------------|
|   |Length:1180987   |Length:1180987   |Length:1180987   |Length:1180987   |Min.   :0.00000 |Length:1180987   |Length:1180987   |
|   |Class :character |Class :character |Class :character |Class :character |1st Qu.:0.00000 |Class :character |Class :character |
|   |Mode  :character |Mode  :character |Mode  :character |Mode  :character |Median :0.00000 |Mode  :character |Mode  :character |
|   |NA               |NA               |NA               |NA               |Mean   :0.06509 |NA               |NA               |
|   |NA               |NA               |NA               |NA               |3rd Qu.:0.00000 |NA               |NA               |
|   |NA               |NA               |NA               |NA               |Max.   :1.00000 |NA               |NA               |



|   |color_is_trans |   quantity     |inv_set_num      |
|:--|:--------------|:---------------|:----------------|
|   |Min.   :0.0000 |Min.   :   1.00 |Length:1180987   |
|   |1st Qu.:1.0000 |1st Qu.:   1.00 |Class :character |
|   |Median :1.0000 |Median :   2.00 |Mode  :character |
|   |Mean   :0.9425 |Mean   :   3.37 |NA               |
|   |3rd Qu.:1.0000 |3rd Qu.:   4.00 |NA               |
|   |Max.   :1.0000 |Max.   :3064.00 |NA               |


# Analiza

## Podstawowa analiza

### Liczebność zestawów

<img src="lego_files/figure-html/analysis-set-amount-1.png" style="display: block; margin: auto;" />

Wykres prezentuje liczbę zestawów powstałych w kolejnych latach.

Widzimy na nim że w latach `1945-1995` były to niewielkie ilości.
Natomiast od roku `2000` nastąpił intensywny przyrost dodawanych zestawów LEGO który cały utrzymuje się do dziś.

### Liczba klocków w zestawach

<img src="lego_files/figure-html/analysis-sets-parts-1.png" style="display: block; margin: auto;" />

<img src="lego_files/figure-html/dd-1.png" style="display: block; margin: auto;" />

Zbiór klocków tworzy 32396 różnych zestawów.

Pierwszy wykres reprezentuje rozproszenie zestawów o określonej ilości elementów. Na wykresie widać, że większość zestawów nie przekracza zawartości 250 klocków.

Drugi wykres przedstawia rozkład **gęstości** zestawów o zadanej liczbie elementów. Ze względu na dużą ilość potencjalnych wartości dane zostały zawężone do zestawów których ilość klocków wystąpiła conajmniej 100 razy.

**Wnioski**
Na wykresie widać że najczęściej występują małe zestawy, nieprzekraczające 15 klocków.

### Liczba minifigurek w zestawach

<img src="lego_files/figure-html/analysis-sets-minifigs-1.png" width="50%" /><img src="lego_files/figure-html/analysis-sets-minifigs-2.png" width="50%" />

Pierwszy wykres reprezentuje rozproszenie zestawów o określonej ilości minifigurek Na wykresie widać, że większość zestawów nie zawiera więcej niż 8 fugurek.

Drugi wykres przedstawia rozkład **gęstości** zestawów o zadanej liczbie minifigurek.
Wyraźnie widać że dominują zestawy z `jedną` figurką. Natomiast duża ich część zawiera nawet do `czterech` minifigur. 

### Liczba części w minifigurkach

<img src="lego_files/figure-html/analysis-minifig-parts-1.png" width="50%" /><img src="lego_files/figure-html/analysis-minifig-parts-2.png" width="50%" />

Zbiór figurek składa się z 13764 rekordów.

Po lewej stronie widzimy rozproszenie minifigurek o określonej ilości elementów. Na wykresie zaobserwować można, że zdecydowana większość skupia się na początku osi X - w skład figurki wchodzi mniej niż 10 części. Za outlayerów można uznać rekordy przekraczajace tą wartość.

Na wykresie po prawej stronie możemy dokładniej przyjrzeć się rozkładowi **gęstość** ilości część składających się na figurki.
Wyraźnie widać że dominują minifigurki `czteroelementowe`. Za nimi drugą wielkość stanowią `pięcioelementowe`.

### Materiały

<img src="lego_files/figure-html/analysis-materials-1.png" style="display: block; margin: auto;" />

Wartość użytego materiału do produkcji klocków nie rozkłada się w żaden sposób. Wyrażnie widać że czynnikiem dominującym w produkcji jest `plastik`.


### Kolory

<img src="lego_files/figure-html/analysis-colors-1.png" width="50%" /><img src="lego_files/figure-html/analysis-colors-2.png" width="50%" /><img src="lego_files/figure-html/analysis-colors-3.png" width="50%" /><img src="lego_files/figure-html/analysis-colors-4.png" width="50%" /><img src="lego_files/figure-html/analysis-colors-5.png" width="50%" /><img src="lego_files/figure-html/analysis-colors-6.png" width="50%" /><img src="lego_files/figure-html/analysis-colors-7.png" width="50%" /><img src="lego_files/figure-html/analysis-colors-8.png" width="50%" /><img src="lego_files/figure-html/analysis-colors-9.png" width="50%" /><img src="lego_files/figure-html/analysis-colors-10.png" width="50%" />

W klockach LEGO zdefiniowano 181 kolorów.
Większość klocków produkowana jest w kolorze `czarnym` i `białym`. W klockach dominuje jednak spora różnorodność kolorystyczna.


## Szczegółowa analiza atrybutów

### Tematy


W zbiorze zestawów pojawiają się braki w wartościach kolumn: `theme`, `parent_theme`.

Z uwagi na to musimy je odfiltorwać, redukując ilość danych z 23501 do 12640 (54% danych jest pełnych). 

<img src="lego_files/figure-html/analysis-sets-themes-1.gif" style="display: block; margin: auto;" />

Na animacji możemy zaobserwować, że w latach 1950-1970 dominowały zestawy o tematyce `System` a od roku 2000 nieprzerwanie zdecydowaną większość stanowią zestawy `Gear`.

### Rozkład klocków według motywów


<img src="lego_files/figure-html/analysis-theme-num-part-i-1.gif" style="display: block; margin: auto;" />

Mimo, że poprzednia sekcja wskazała na `system` oraz `gear` jako najczęściej występujce tematycznie zestawy to powyższy wykres nie wskazuje aby dominowały pod względem ilości klocków.

Najbardziej wyróżnia się tematyka `Star Wars` która od `2015` dominuje pod względem liczebności klocków budujących zestawy.

**Wnioski**
Popularność zestawów nie idzie w parze z ich wielkością.

<img src="lego_files/figure-html/analysis-theme-num-part-ii-1.gif" style="display: block; margin: auto;" />

Dodatkowo powyższy boxplot cały czas przesunięty jest znacznie w stronę 0.
Spowodowane jest to pewną rzadkością w liczebności elementów w motywach. Wynikać to może najpewniej z sezonowości tematów jakie są wypuszczane przez firmę i okresowym zainteresowaniem nimi przez ludzi. 

Motywy klocków w dużej części związane są z popularnymi książkami, filmami czy serialami. Wzrosty tematów na wykresach pokrywają sie w natrualny sposob czasowo z datami nowych premier. Wynika stąd, że klocki LEGO podążają za trendami kulturowymi.

### Rozkład klocków według kolorów





<img src="lego_files/figure-html/analysis-color-num-part-i-1.gif" style="display: block; margin: auto;" />

Animacja pokazuje, rozkład kolorów wśród produkowanych klocków w poszczególnych latach. Ze względu na dużą ilość dostępnych kolorów (181 kolorów) zostały wybrane tylko te powyżej 200 klocków.

Widać, że od roku `2000` nastąpił znaczący wzrost używanych kolorów co pokrywa się ze wzrostem liczby produkowanych zestawów z sekcji '*Liczebność zestawów*'.

### Analiza korelacji między zmiennymi

Poniżej znajduje się tabela zawierające współczynniki korelacji pearsona dla zestawów i tworzących je klocków.


|               | category_name| part_material| is_spare| color_name| color_rgb| color_is_trans| inventory_id| theme| theme_parent| decade|
|:--------------|-------------:|-------------:|--------:|----------:|---------:|--------------:|------------:|-----:|------------:|------:|
|category_name  |          1.00|          0.02|     0.09|      -0.08|     -0.08|          -0.04|        -0.01|  0.05|         0.01|   0.11|
|part_material  |          0.02|          1.00|     0.01|       0.03|      0.03|          -0.01|        -0.04|  0.00|         0.01|  -0.01|
|is_spare       |          0.09|          0.01|     1.00|       0.04|      0.03|          -0.16|         0.03|  0.01|        -0.05|   0.12|
|color_name     |         -0.08|          0.03|     0.04|       1.00|      0.88|          -0.28|         0.00| -0.05|         0.01|  -0.08|
|color_rgb      |         -0.08|          0.03|     0.03|       0.88|      1.00|          -0.16|         0.01| -0.04|         0.00|  -0.05|
|color_is_trans |         -0.04|         -0.01|    -0.16|      -0.28|     -0.16|           1.00|         0.02|  0.00|         0.01|  -0.02|
|inventory_id   |         -0.01|         -0.04|     0.03|       0.00|      0.01|           0.02|         1.00|  0.04|        -0.14|   0.31|
|theme          |          0.05|          0.00|     0.01|      -0.05|     -0.04|           0.00|         0.04|  1.00|        -0.06|   0.14|
|theme_parent   |          0.01|          0.01|    -0.05|       0.01|      0.00|           0.01|        -0.14| -0.06|         1.00|  -0.39|
|decade         |          0.11|         -0.01|     0.12|      -0.08|     -0.05|          -0.02|         0.31|  0.14|        -0.39|   1.00|

Na podstawie danych trudno dojrzeć silniejsze związki (z wartością współczynnika korelacji pearsona powyżej 0.5, bądź poniżej -0.5) pomiędzy którymikolwiek nieoczywistymi wartościami. 

Widoczna jest jedynie zależność:

- **`color_name`** oraz **`color_rgb`**: *0.88*

# Predykcja produkcji klocka

W naszej analizie przygotujemy 4 modele do przewidywania dekady produkcji klocka, na tych samych danych.

## Dane


Dane do uczenia dzielimy na 3 zbiory:

- treningowy - na którym odbędzie się uczenie (75% całego zbioru danych)
- testowy - na którym będzie sprawdzana wydajność modelu (25% całego zbioru danych)
- kontrolny - określony poprzez powtórną krosswalidacje


## Linear Regression

```
## Linear Regression 
## 
## 332404 samples
##     11 predictor
## 
## Pre-processing: centered (11), scaled (11) 
## Resampling: Cross-Validated (2 fold, repeated 5 times) 
## Summary of sample sizes: 166202, 166202, 166202, 166202, 166201, 166203, ... 
## Resampling results across tuning parameters:
## 
##   intercept  RMSE          Rsquared  MAE         
##   FALSE      2.004169e+03  1         2.004169e+03
##    TRUE      1.128673e-09  1         1.128654e-09
## 
## RMSE was used to select the optimal model using the smallest value.
## The final value used for the model was intercept = TRUE.
```


```{=html}
<div class="plotly html-widget html-fill-item" id="htmlwidget-31ff42c34ff473fe07bd" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-31ff42c34ff473fe07bd">{"x":{"data":[{"orientation":"h","width":[0.89999999999999858,0.89999999999999858,0.89999999999999947,0.90000000000000036,0.90000000000000036,0.90000000000000036,0.90000000000000036,0.90000000000000036,0.90000000000000013,0.89999999999999991],"base":[0,0,0,0,0,0,0,0,0,0],"x":[100,6.8039825267274051e-11,2.6755401678217812e-11,2.630262235683221e-11,1.1598085946921189e-11,1.0920100674537396e-11,9.0511043785228594e-12,7.7095041223901989e-12,2.3923690444034463e-13,0],"y":[10,9,8,7,6,5,4,3,2,1],"text":["Feature: decade_end<br />Importance: 1.000000e+02","Feature: inventory_id<br />Importance: 6.803983e-11","Feature: theme_parent<br />Importance: 2.675540e-11","Feature: category_name<br />Importance: 2.630262e-11","Feature: color_name<br />Importance: 1.159809e-11","Feature: color_rgb<br />Importance: 1.092010e-11","Feature: theme<br />Importance: 9.051104e-12","Feature: is_spare<br />Importance: 7.709504e-12","Feature: color_is_trans<br />Importance: 2.392369e-13","Feature: part_material<br />Importance: 0.000000e+00"],"type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(89,89,89,1)","line":{"width":1.8897637795275593,"color":"transparent"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.228310502283104,"r":7.3059360730593621,"b":40.182648401826491,"l":107.39726027397263},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-5,105],"tickmode":"array","ticktext":["0","25","50","75","100"],"tickvals":[0,24.999999999999996,50,75,100],"categoryorder":"array","categoryarray":["0","25","50","75","100"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.6529680365296811,"tickwidth":0.66417600664176002,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.68949771689498},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176002,"zeroline":false,"anchor":"y","title":{"text":"Importance","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.40000000000000002,10.6],"tickmode":"array","ticktext":["part_material","color_is_trans","is_spare","theme","color_rgb","color_name","category_name","theme_parent","inventory_id","decade_end"],"tickvals":[1,2,3,4,5,6.0000000000000009,7,8,9,10],"categoryorder":"array","categoryarray":["part_material","color_is_trans","is_spare","theme","color_rgb","color_name","category_name","theme_parent","inventory_id","decade_end"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.6529680365296811,"tickwidth":0.66417600664176002,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.68949771689498},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176002,"zeroline":false,"anchor":"x","title":{"text":"Feature","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.8897637795275593,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.68949771689498}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"1f1c5835428e":{"x":{},"y":{},"type":"bar"}},"cur_data":"1f1c5835428e","visdat":{"1f1c5835428e":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.20000000000000001,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```


## RIDGE

```
## Ridge Regression 
## 
## 332404 samples
##     11 predictor
## 
## Pre-processing: centered (11), scaled (11) 
## Resampling: Cross-Validated (2 fold, repeated 5 times) 
## Summary of sample sizes: 166202, 166202, 166203, 166201, 166203, 166201, ... 
## Resampling results across tuning parameters:
## 
##   lambda     RMSE          Rsquared   MAE         
##   0.0000000  1.211535e-11  1.0000000  9.385350e-12
##   0.2631579  1.860252e+00  0.9967425  1.501140e+00
##   0.5263158  3.380620e+00  0.9917727  2.725060e+00
##   0.7894737  4.651552e+00  0.9872624  3.746991e+00
##   1.0526316  5.731139e+00  0.9834738  4.614479e+00
##   1.3157895  6.660051e+00  0.9803294  5.360595e+00
##   1.5789474  7.467979e+00  0.9777071  6.009347e+00
##   1.8421053  8.177208e+00  0.9754991  6.578709e+00
##   2.1052632  8.804833e+00  0.9736203  7.082474e+00
##   2.3684211  9.364198e+00  0.9720052  7.531387e+00
##   2.6315789  9.865881e+00  0.9706036  7.933967e+00
##   2.8947368  1.031838e+01  0.9693767  8.297045e+00
##   3.1578947  1.072859e+01  0.9682943  8.626174e+00
##   3.4210526  1.110218e+01  0.9673328  8.925906e+00
##   3.6842105  1.144384e+01  0.9664732  9.200012e+00
##   3.9473684  1.175751e+01  0.9657002  9.451644e+00
##   4.2105263  1.204650e+01  0.9650016  9.683460e+00
##   4.4736842  1.231359e+01  0.9643670  9.897711e+00
##   4.7368421  1.256120e+01  0.9637883  1.009632e+01
##   5.0000000  1.279138e+01  0.9632583  1.028095e+01
## 
## RMSE was used to select the optimal model using the smallest value.
## The final value used for the model was lambda = 0.
```


```{=html}
<div class="plotly html-widget html-fill-item" id="htmlwidget-0b4ab69dd999c59e40ac" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-0b4ab69dd999c59e40ac">{"x":{"data":[{"x":[0,0.26315789473684209,0.52631578947368418,0.78947368421052633,1.0526315789473684,1.3157894736842104,1.5789473684210527,1.8421052631578947,2.1052631578947367,2.3684210526315788,2.6315789473684208,2.8947368421052628,3.1578947368421053,3.4210526315789473,3.6842105263157894,3.9473684210526314,4.2105263157894735,4.4736842105263159,4.7368421052631575,5],"y":[1.2115345005034441e-11,1.860252263158541,3.380620288434407,4.651552239959142,5.7311386075703687,6.6600511938682656,7.4679788541091812,8.1772081875406819,8.8048329426033902,9.364198180510769,9.8658810265818619,10.31837602172692,10.728585203592386,11.102175424253412,11.443843294721653,11.757514581440034,12.046496283272914,12.313594022182842,12.561203656243672,12.791383495156225],"text":["lambda: 0.0000000<br />RMSE: 1.211535e-11","lambda: 0.2631579<br />RMSE: 1.860252e+00","lambda: 0.5263158<br />RMSE: 3.380620e+00","lambda: 0.7894737<br />RMSE: 4.651552e+00","lambda: 1.0526316<br />RMSE: 5.731139e+00","lambda: 1.3157895<br />RMSE: 6.660051e+00","lambda: 1.5789474<br />RMSE: 7.467979e+00","lambda: 1.8421053<br />RMSE: 8.177208e+00","lambda: 2.1052632<br />RMSE: 8.804833e+00","lambda: 2.3684211<br />RMSE: 9.364198e+00","lambda: 2.6315789<br />RMSE: 9.865881e+00","lambda: 2.8947368<br />RMSE: 1.031838e+01","lambda: 3.1578947<br />RMSE: 1.072859e+01","lambda: 3.4210526<br />RMSE: 1.110218e+01","lambda: 3.6842105<br />RMSE: 1.144384e+01","lambda: 3.9473684<br />RMSE: 1.175751e+01","lambda: 4.2105263<br />RMSE: 1.204650e+01","lambda: 4.4736842<br />RMSE: 1.231359e+01","lambda: 4.7368421<br />RMSE: 1.256120e+01","lambda: 5.0000000<br />RMSE: 1.279138e+01"],"type":"scatter","mode":"markers+lines","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.6692913385826778,"symbol":"circle","line":{"width":1.8897637795275593,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","line":{"width":1.8897637795275593,"color":"rgba(0,0,0,1)","dash":"solid"},"frame":null}],"layout":{"margin":{"t":26.228310502283104,"r":7.3059360730593621,"b":40.182648401826491,"l":37.260273972602747},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-0.25,5.25],"tickmode":"array","ticktext":["0","1","2","3","4","5"],"tickvals":[0,1,2,3,4,5],"categoryorder":"array","categoryarray":["0","1","2","3","4","5"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.6529680365296811,"tickwidth":0.66417600664176002,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.68949771689498},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176002,"zeroline":false,"anchor":"y","title":{"text":"Weight Decay","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-0.63956917474509023,13.430952669913431],"tickmode":"array","ticktext":["0","5","10"],"tickvals":[0,5,10],"categoryorder":"array","categoryarray":["0","5","10"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.6529680365296811,"tickwidth":0.66417600664176002,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.68949771689498},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176002,"zeroline":false,"anchor":"x","title":{"text":"RMSE (Repeated Cross-Validation)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.8897637795275593,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.68949771689498}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"1f1c74956638":{"x":{},"y":{},"type":"scatter"},"1f1c63575494":{"x":{},"y":{}}},"cur_data":"1f1c74956638","visdat":{"1f1c74956638":["function (y) ","x"],"1f1c63575494":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.20000000000000001,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```


```{=html}
<div class="plotly html-widget html-fill-item" id="htmlwidget-2dacbc9e492e918df99c" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-2dacbc9e492e918df99c">{"x":{"data":[{"orientation":"h","width":[0.89999999999999858,0.89999999999999858,0.89999999999999858,0.89999999999999947,0.90000000000000036,0.90000000000000036,0.90000000000000036,0.90000000000000036,0.90000000000000036,0.90000000000000013,0.89999999999999991],"base":[0,0,0,0,0,0,0,0,0,0,0],"x":[100,100,14.99494756458572,9.5884730940225005,1.9137059711471911,1.5324673984318991,1.2894900790180563,0.54152934843147726,0.2112324292465656,0.04858060808780014,0],"y":[11,10,9,8,7,6,5,4,3,2,1],"text":["Feature: decade_end<br />Importance: 100.00000000","Feature: decade<br />Importance: 100.00000000","Feature: theme_parent<br />Importance:  14.99494756","Feature: inventory_id<br />Importance:   9.58847309","Feature: theme<br />Importance:   1.91370597","Feature: is_spare<br />Importance:   1.53246740","Feature: category_name<br />Importance:   1.28949008","Feature: color_name<br />Importance:   0.54152935","Feature: color_rgb<br />Importance:   0.21123243","Feature: color_is_trans<br />Importance:   0.04858061","Feature: part_material<br />Importance:   0.00000000"],"type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(89,89,89,1)","line":{"width":1.8897637795275593,"color":"transparent"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.228310502283104,"r":7.3059360730593621,"b":40.182648401826491,"l":107.39726027397263},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-5,105],"tickmode":"array","ticktext":["0","25","50","75","100"],"tickvals":[0,24.999999999999996,50,75,100],"categoryorder":"array","categoryarray":["0","25","50","75","100"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.6529680365296811,"tickwidth":0.66417600664176002,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.68949771689498},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176002,"zeroline":false,"anchor":"y","title":{"text":"Importance","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.40000000000000002,11.6],"tickmode":"array","ticktext":["part_material","color_is_trans","color_rgb","color_name","category_name","is_spare","theme","inventory_id","theme_parent","decade","decade_end"],"tickvals":[1,2,3,4,5,6,7,8,9,10,11],"categoryorder":"array","categoryarray":["part_material","color_is_trans","color_rgb","color_name","category_name","is_spare","theme","inventory_id","theme_parent","decade","decade_end"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.6529680365296811,"tickwidth":0.66417600664176002,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.68949771689498},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176002,"zeroline":false,"anchor":"x","title":{"text":"Feature","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.8897637795275593,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.68949771689498}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"1f1c6a9c4a44":{"x":{},"y":{},"type":"bar"}},"cur_data":"1f1c6a9c4a44","visdat":{"1f1c6a9c4a44":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.20000000000000001,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```

## LASSO

```
## The lasso 
## 
## 332404 samples
##      9 predictor
## 
## Pre-processing: centered (9), scaled (9) 
## Resampling: Cross-Validated (2 fold, repeated 5 times) 
## Summary of sample sizes: 166203, 166201, 166202, 166202, 166203, 166201, ... 
## Resampling results across tuning parameters:
## 
##   fraction    RMSE      Rsquared   MAE     
##   0.00000000  2.723849        NaN  2.171990
##   0.05263158  2.664815  0.1500519  2.111360
##   0.10526316  2.614110  0.1763430  2.069160
##   0.15789474  2.568845  0.2007261  2.030195
##   0.21052632  2.528762  0.2101168  1.992892
##   0.26315789  2.494111  0.2141952  1.959603
##   0.31578947  2.465121  0.2161166  1.929600
##   0.36842105  2.441929  0.2194018  1.903174
##   0.42105263  2.422481  0.2286319  1.881675
##   0.47368421  2.405594  0.2362056  1.862792
##   0.52631579  2.391216  0.2416570  1.846067
##   0.57894737  2.379239  0.2462800  1.832375
##   0.63157895  2.369408  0.2496883  1.820660
##   0.68421053  2.361756  0.2519919  1.811079
##   0.73684211  2.356307  0.2534376  1.803666
##   0.78947368  2.352854  0.2545131  1.799032
##   0.84210526  2.351030  0.2552233  1.796449
##   0.89473684  2.349872  0.2558512  1.794837
##   0.94736842  2.349183  0.2562139  1.793652
##   1.00000000  2.348972  0.2563208  1.792926
## 
## RMSE was used to select the optimal model using the smallest value.
## The final value used for the model was fraction = 1.
```


```{=html}
<div class="plotly html-widget html-fill-item" id="htmlwidget-dfe6fbca38e1f1742184" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-dfe6fbca38e1f1742184">{"x":{"data":[{"x":[0,0.052631578947368418,0.10526315789473684,0.15789473684210525,0.21052631578947367,0.26315789473684209,0.31578947368421051,0.36842105263157893,0.42105263157894735,0.47368421052631576,0.52631578947368418,0.57894736842105265,0.63157894736842102,0.68421052631578938,0.73684210526315785,0.78947368421052633,0.84210526315789469,0.89473684210526305,0.94736842105263153,1],"y":[2.7238488705203325,2.6648147553040369,2.6141098306124309,2.5688449949539534,2.5287621496380419,2.4941111667954097,2.4651211310215122,2.4419287964465175,2.4224814804730519,2.4055944570627514,2.3912159145990008,2.3792385783472403,2.369407973098864,2.3617562808760062,2.3563072373847103,2.3528538629336735,2.3510303486169848,2.3498720402460425,2.3491829757621652,2.3489718049783335],"text":["fraction: 0.00000000<br />RMSE: 2.723849","fraction: 0.05263158<br />RMSE: 2.664815","fraction: 0.10526316<br />RMSE: 2.614110","fraction: 0.15789474<br />RMSE: 2.568845","fraction: 0.21052632<br />RMSE: 2.528762","fraction: 0.26315789<br />RMSE: 2.494111","fraction: 0.31578947<br />RMSE: 2.465121","fraction: 0.36842105<br />RMSE: 2.441929","fraction: 0.42105263<br />RMSE: 2.422481","fraction: 0.47368421<br />RMSE: 2.405594","fraction: 0.52631579<br />RMSE: 2.391216","fraction: 0.57894737<br />RMSE: 2.379239","fraction: 0.63157895<br />RMSE: 2.369408","fraction: 0.68421053<br />RMSE: 2.361756","fraction: 0.73684211<br />RMSE: 2.356307","fraction: 0.78947368<br />RMSE: 2.352854","fraction: 0.84210526<br />RMSE: 2.351030","fraction: 0.89473684<br />RMSE: 2.349872","fraction: 0.94736842<br />RMSE: 2.349183","fraction: 1.00000000<br />RMSE: 2.348972"],"type":"scatter","mode":"markers+lines","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.6692913385826778,"symbol":"circle","line":{"width":1.8897637795275593,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","line":{"width":1.8897637795275593,"color":"rgba(0,0,0,1)","dash":"solid"},"frame":null}],"layout":{"margin":{"t":26.228310502283104,"r":7.3059360730593621,"b":40.182648401826491,"l":43.105022831050235},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-0.050000000000000003,1.05],"tickmode":"array","ticktext":["0.00","0.25","0.50","0.75","1.00"],"tickvals":[0,0.25,0.5,0.75,1],"categoryorder":"array","categoryarray":["0.00","0.25","0.50","0.75","1.00"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.6529680365296811,"tickwidth":0.66417600664176002,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.68949771689498},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176002,"zeroline":false,"anchor":"y","title":{"text":"Fraction of Full Solution","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[2.3302279517012336,2.7425927237974324],"tickmode":"array","ticktext":["2.4","2.5","2.6","2.7"],"tickvals":[2.4000000000000004,2.5000000000000004,2.6000000000000005,2.7000000000000002],"categoryorder":"array","categoryarray":["2.4","2.5","2.6","2.7"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.6529680365296811,"tickwidth":0.66417600664176002,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.68949771689498},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176002,"zeroline":false,"anchor":"x","title":{"text":"RMSE (Repeated Cross-Validation)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.8897637795275593,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.68949771689498}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"1f1c3985439":{"x":{},"y":{},"type":"scatter"},"1f1c53783409":{"x":{},"y":{}}},"cur_data":"1f1c3985439","visdat":{"1f1c3985439":["function (y) ","x"],"1f1c53783409":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.20000000000000001,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```


```{=html}
<div class="plotly html-widget html-fill-item" id="htmlwidget-392611703cc4d123a26c" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-392611703cc4d123a26c">{"x":{"data":[{"orientation":"h","width":[0.89999999999999858,0.89999999999999947,0.90000000000000036,0.90000000000000036,0.90000000000000036,0.90000000000000036,0.90000000000000036,0.90000000000000013,0.89999999999999991],"base":[0,0,0,0,0,0,0,0,0],"x":[100,63.944692388859856,12.762338533718953,10.219891679052441,8.5994970869735727,3.6114120845811364,1.4086906828591359,0.32397984640237232,0],"y":[9,8,7,6,5,4,3,2,1],"text":["Feature: theme_parent<br />Importance: 100.0000000","Feature: inventory_id<br />Importance:  63.9446924","Feature: theme<br />Importance:  12.7623385","Feature: is_spare<br />Importance:  10.2198917","Feature: category_name<br />Importance:   8.5994971","Feature: color_name<br />Importance:   3.6114121","Feature: color_rgb<br />Importance:   1.4086907","Feature: color_is_trans<br />Importance:   0.3239798","Feature: part_material<br />Importance:   0.0000000"],"type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(89,89,89,1)","line":{"width":1.8897637795275593,"color":"transparent"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.228310502283104,"r":7.3059360730593621,"b":40.182648401826491,"l":107.39726027397263},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-5,105],"tickmode":"array","ticktext":["0","25","50","75","100"],"tickvals":[0,24.999999999999996,50,75,100],"categoryorder":"array","categoryarray":["0","25","50","75","100"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.6529680365296811,"tickwidth":0.66417600664176002,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.68949771689498},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176002,"zeroline":false,"anchor":"y","title":{"text":"Importance","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.40000000000000002,9.5999999999999996],"tickmode":"array","ticktext":["part_material","color_is_trans","color_rgb","color_name","category_name","is_spare","theme","inventory_id","theme_parent"],"tickvals":[1,2,3,4,5,6,6.9999999999999991,8,9],"categoryorder":"array","categoryarray":["part_material","color_is_trans","color_rgb","color_name","category_name","is_spare","theme","inventory_id","theme_parent"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.6529680365296811,"tickwidth":0.66417600664176002,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.68949771689498},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176002,"zeroline":false,"anchor":"x","title":{"text":"Feature","font":{"color":"rgba(0,0,0,1)","family":"","size":14.611872146118724}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.8897637795275593,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.68949771689498}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"1f1c5b246188":{"x":{},"y":{},"type":"bar"}},"cur_data":"1f1c5b246188","visdat":{"1f1c5b246188":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.20000000000000001,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```


## Porównanie


```
## 
## Call:
## summary.resamples(object = models)
## 
## Models: lm, ridge, lasso 
## Number of resamples: 10 
## 
## MAE 
##               Min.      1st Qu.       Median         Mean      3rd Qu.
## lm    6.283148e-10 6.912554e-10 8.256736e-10 1.128654e-09 1.722941e-09
## ridge 1.818989e-12 4.026745e-12 7.728547e-12 9.385350e-12 1.432024e-11
## lasso 1.789059e+00 1.791057e+00 1.792923e+00 1.792926e+00 1.794797e+00
##               Max. NA's
## lm    2.031484e-09    0
## ridge 2.335249e-11    0
## lasso 1.796774e+00    0
## 
## RMSE 
##               Min.      1st Qu.       Median         Mean      3rd Qu.
## lm    6.283248e-10 6.912661e-10 8.256872e-10 1.128673e-09 1.722966e-09
## ridge 1.818989e-12 4.488663e-12 1.025589e-11 1.211535e-11 1.881707e-11
## lasso 2.344629e+00 2.345819e+00 2.348968e+00 2.348972e+00 2.352102e+00
##               Max. NA's
## lm    2.031517e-09    0
## ridge 2.979116e-11    0
## lasso 2.353309e+00    0
## 
## Rsquared 
##            Min.   1st Qu.    Median      Mean   3rd Qu.      Max. NA's
## lm    1.0000000 1.0000000 1.0000000 1.0000000 1.0000000 1.0000000    0
## ridge 1.0000000 1.0000000 1.0000000 1.0000000 1.0000000 1.0000000    0
## lasso 0.2542657 0.2552093 0.2563155 0.2563208 0.2574335 0.2584049    0
```






