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


## proyeksi ##
```
Affine transformasi
[x', y', 1]=[[a, b, c],
             [d, e, f],
             [0, 0, 1]] @ [x, y, 1]

projective transformasi
[x', y', 1]=[[a, b, c],
             [d, e, f],
             [g, h, 1]] @ [x, y, 1]
```





