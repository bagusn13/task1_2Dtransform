###### Bagus Nugraha ######
###### 1313617002 ######
###### Sistem Pakar Semester 112 ######
###### Assignment 1 Task 1 2D Transformations ######

laporan ini disusun untuk memenuhi *task 1 asssignment1*, diminta untuk beberapa tranfornasi sederhana dalam bidang dua dimensi. saya menulis kode di jupyter notebook dengan python 3.

## Translasi ##
Translasi atau pergeseran adalah transformasi yang memindahkan titik dengan jarak dan arah tertentu. translasi dinyatakan oleh T = (tx,ty) dengan tx menyatakn jarak dan arah perpindahan secara horizontal dan ty menyatakan jarak dan arah perpindahan secara vertikal.

Jika A(x,y) di translasikan oleh T = (tx,ty), akan diperoleh bayangan A'(x',y') dengan x' = x + tx dan y' = y + ty. Atau A' = [I t]A

```
A' = [[1, 0, tx],
      [0, 1, ty]] @ A
```

Dimana I adalah matriks identitas 2x2. Dikarenakan kita menggunakan *homogeneous coordinates* yang mana A(x,y,1). Untuk dimungkinkannya transformasi menggunakan perkalian matriks maka menggunakan matriks 3x3 (didapat dari matriks 2x3 dengan menambahkan baris [0, 0, 1]). Sehingga matriksnya:

```
A' = [[1, 0, tx],
      [0, 1, ty],
      [0, 0, 1 ]] @ A
     
[x',y',1] = [[1, 0, tx],
             [0, 1, ty],
             [0, 0, 1 ]] @ [x, y, 1]
```

## Rotasi ##
Rotasi adalah transformasi yang memindahkan titik-titik dengan memutar titik-titik tersebut sejauh theta. Jika theta positif, arah putaran berlawanan dengan arah putaran jarum jam. Jika theta negatif, arah putaran searah dengan putaran jarum jam.

Jika titik A(x,y) dirotasikan sejauh theta akan diperoleh bayangan A'(x', y') dengan x' = xcos(theta) - ysin(theta) dan y' = xsin(theta) + ycos(theta)

## Rotasi + Translasi ##
Transformasi ini juga dikenal dengan *2d euclidean transformation*.

Dapat ditulis dengan x' = Rx + t dimana R:
```
R = [[cos(theta), -sin(theta)],
     [sin(theta), cos(theta)]]
```
maka x' = (xcostheta) - ysin(theta)) + tx dan y' = (xsin(theta) + ycos(theta)) + ty 
```
[x', y', 1] = [[cos, -sin, tx],
               [sin,  cos, ty], 
               [0  ,  0  , 1 ]] @ [x, y, 1]
```

## Dilatasi ##
Dilatasi adalah suatu transformasi yang mengubah ukuran (memperbesar atau memperkecil) suatu bangun geometri, tetapi tidak mengubah bentuk bangun geometri tersebut.

Jika A(x,y) didilatasikan dengan faktor skala k maka diperoleh bayangan A'(x',y') dengan x' = kx dan y' = ky.

## Affine ##
Transformasi ini kombinasi dari translasi, rotasi, dan dilatasi. Transformasi ini dapat dinyatakan sebagai x' = sRx + tx dan y' = sRy + ty atau x' = s(xcos(theta) - ysin(theta)) + tx dan y' = s(xsin(theta) + ycos(theta)) + ty (dimana s adalah faktor skala). Dari persamaan tersebut dapat kita nyatakan dalam matriks : (@ operator perkalian matriks)
```
affine_matrix = [[s.cos, -s.sin, tx],
                 [s.sin,  s.cos, ty],
                 [0    ,  0    , 1 ]]
                 
[x', y', 1] = affine_matrix @ [x, y, 1]
```


## Proyeksi ##
Proyeksi adalah transformasi linier pada vektor homogen yang diwakili oleh matriks 3×3 non-singular. matriks non-singular adalah matriksyang bisa diinvers yang mana nilai determinan dari matriks tersebut tidak sama dengan 0. kita bisa menuliskan persamaannya menjadi x' = H x

kita dapat menyatakan matriks proyeksi sebagai berikut:
```
projective transformasi
[x', y', 1]=[[a11, a12, a13],
             [a21, a22, a23],
             [a31, a32, v  ]] @ [x, y, 1]
```
Projective transformation itu punya 8 derajat kebebasan dikarenakan v = 1 atau 0. dari web bla  bla bla, projective matriks dapat kita sederhanakan menjadi:
```
projective transformasi
[wx', wy', w]=[[1,   0, 0],
               [0,   1, 0],
               [v1, v2, v]] @ [x, y, 1]
```
kenapa bisa begitu? di karenakan bagian kiri atas 4 derajat kebebasan dari komponen affine, bagian atas kanan 2 derajat kebebasan dari komponen translasi, dan menyisakan 2 derajat kebebasan yang baru yaitu v1 dan v2. karena baris ketiga juga dipakai dalam matriks projective maka hasil yang didapat tidak langsung berupa koordinat melainkan [wx,wy,w], yang mana titik tersebut bukan berada di dimensi 2 melainkan berada di dimensi 3, disinilah asal kata projeksi.

dari matriks diatas dapat kita evaluasi menjadi [wx', wy', w] = [x, y, (v1x + v2y + v)]
dengan w = v1x + v2y + v maka didapat x' = x/(v1x + v2y + v) dan y' = y/(v1x + v2y + v)



