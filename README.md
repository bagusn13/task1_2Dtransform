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
      [0, 1, ty]] x A
```

Dimana I adalah matriks identitas 2x2. Dikarenakan kita menggunakan *homogeneous coordinates* yang mana A(x,y,1). Untuk dimungkinkannya transformasi menggunakan perkalian matriks maka menggunakan matriks 3x3 (didapat dari matriks 2x3 dengan menambahkan baris [0, 0, 1]). Sehingga matriksnya:

```
A' = [[1, 0, tx],
      [0, 1, ty],
      [0, 0, 1 ]] x A
     
[x',y',1] = [[1, 0, tx],
             [0, 1, ty],
             [0, 0, 1 ]] x [x, y, 1]
```


```python
A_aksen = np.array([I, t])@A
```

```python
A_aksen = np.array([[I,             t],
                    [0.transpose(), 1]])@A
```




2. rotasi
3. skala
4. affine
5. proyeksi



