# Ejercicios prácticos SQL

| producto                  |
| ------------------------- |
| codigo INT(10)            |
| nombre VARCHAR(100)       |
| precio DOUBLE             |
| codigo_fabricante INT(10) |

| fabricante          |
| ------------------- |
| codigo INT(10)      |
| nombre VARCHAR(100) |

**1. Realice la inserción de los siguientes datos:**

   abricante (1, 'Asus');  
   
   abricante (2, 'Lenovo');  
   
   abricante (3, 'Hewlett-Packard'); 
   
   abricante (4, 'Samsung');  
   
   abricante (5, 'Seagate');  
   
   abricante (6, 'Crucial');  
   
   abricante (7, 'Gigabyte');  
   
   abricante (8, 'Huawei');  
   
   abricante (9, 'xiaomi');
   
   producto (1, 'Disco duro ЅАТАЗ 1TB', 86.99, 5); 
   
   producto (2, 'Memoria RAM DDR4 8GB', 120, 6); 
   
   producto  producto (3, 'Disco SSD 1 TB', 150.99, 4);  
   
   producto (4, 'GeForce GTX 1050Ti', 185, 7); 
   
   producto (5, 'GeForce GTX 1080 Xtreme', 755, 6); 
   
   producto (6, producto 'Monitor 24 LED Full HD', 202, 1);  
   
   producto (7, producto 'Monitor 27 LED Full HD', 245.99, 1);  
   
   producto (8, 'Portátil Yoga 520', 559, 2); 
   
   producto (9, 'Portátil Ideapd 320', 444, 2); 
   
   producto (10, 'Impresora HP Deskjet 3720', 59.99, 3);  
   
   producto (11, 'Impresora HP Laserjet Pro M26nw , 180, 3);

```sql
INSERT INTO fabricante (codigo, nombre) VALUES
(1, 'Asus'),
(2, 'Lenovo'),
(3, 'Hewlett-Packard'),
(4, 'Samsung'),
(5, 'Seagate'),
(6, 'Crucial'),
(7, 'Gigabyte'),
(8, 'Huawei'),
(9, 'Xiaomi');

INSERT INTO producto (codigo, nombre, precio, codigo_fabricante) VALUES
(1, 'Disco duro SATA3 1TB', 86.99, 5),
(2, 'Memoria RAM DDR4 8GB', 120, 6),
(3, 'Disco SSD 1 TB', 150.99, 4),
(4, 'GeForce GTX 1050Ti', 185, 7),
(5, 'GeForce GTX 1080 Xtreme', 755, 6),
(6, 'Monitor 24 LED Full HD', 202, 1),
(7, 'Monitor 27 LED Full HD', 245.99, 1),
(8, 'Portátil Yoga 520', 559, 2),
(9, 'Portátil Ideapad 320', 444, 2),
(10, 'Impresora HP Deskjet 3720', 59.99, 3),
(11, 'Impresora HP Laserjet Pro M26nw', 180, 3);

```
---

**2. Realice las siguientes consultas:**

2.1. Lista el nombre de todos los productos que hay en la tabla producto.
```sql
SELECT nombre FROM producto;
```
2.2. Lista los nombres y los precios de todos los productos de la tabla producto.
```sql
SELECT nombre, precio FROM producto;

```
2.3. Lista todas las columnas de la tabla producto.
```sql
SELECT nombre, precio FROM producto;

```
2.4. Lista el nombre de los productos, el precio en euros y el precio en dólares estadounidenses (USD).
```sql
SELECT nombre, precio, precio * 0.85 AS USD FROM producto;

```
2.5. Lista el nombre de los productos, el precio en euros y el precio en dólares estadounidenses (USD). Utiliza los siguientes alias para las columnas: nombre
de producto, euros, dólares.
```sql
SELECT nombre AS "nombre de producto", precio AS euros, precio * 0.85 AS dólares FROM producto;

```
2.6. Lista los nombres y los precios de todos los productos de la tabla producto, convirtiendo los nombres a mayúscula.
```sql
SELECT UPPER(nombre), precio FROM producto;

```
2.7. Lista los nombres y los precios de todos los productos de la tabla producto, convirtiendo los nombres a minúscula.
```sql
SELECT LOWER(nombre), precio FROM producto;

```
2.8. Lista el nombre de todos los fabricantes en una columna, y en otra columna obtenga en mayúsculas los dos primeros caracteres del nombre del fabricante.
```sql
SELECT nombre, UPPER(SUBSTR(nombre, 1, 2)) AS dos_primeras FROM fabricante;

```
2.9. Lista los nombres y los precios de todos los productos de la tabla producto, redondeando el valor del precio.
```sql
SELECT nombre, ROUND(precio) FROM producto;

```
2.10. Lista los nombres y los precios de todos los productos de la tabla producto, truncando el valor del precio para mostrarlo sin ninguna cifra decimal.
```sql
SELECT nombre, TRUNCATE(precio, 0) FROM producto;

```
2.11. Lista el identificador de los fabricantes que tienen productos en la tabla producto.
```sql
SELECT DISTINCT codigo_fabricante FROM producto;

```
2.12. Lista el identificador de los fabricantes que tienen productos en la tabla producto, eliminando los identificadores que aparecen repetidos.
```sql
SELECT DISTINCT codigo_fabricante FROM producto;

```
2.13. Lista los nombres de los fabricantes ordenados de forma ascendente.
```sql
SELECT nombre FROM fabricante ORDER BY nombre ASC;

```
2.14. Lista los nombres de los fabricantes ordenados de forma descendente.
```sql
SELECT nombre FROM fabricante ORDER BY nombre DESC;

```
2.15. Lista los nombres de los productos ordenados en primer lugar por el nombre de forma ascendente y en segundo lugar por el precio de forma
descendente.
```sql
SELECT nombre, precio FROM producto ORDER BY nombre ASC, precio DESC;

```
2.16. Devuelve una lista con las 5 primeras filas de la tabla fabricante.
```sql
SELECT * FROM fabricante LIMIT 5;

```

2.17. Devuelve una lista con 2 filas a partir de la cuarta fila de la tabla fabricante. La cuarta fila también se debe incluir en la respuesta.
```sql
SELECT * FROM fabricante LIMIT 2 OFFSET 3;

```
2.18. Lista el nombre y el precio del producto más barato. (Utilice solamente las cláusulas ORDER BY y LIMIT)
```sql
SELECT nombre, precio FROM producto ORDER BY precio ASC LIMIT 1;

```
2.19. Lista el nombre y el precio del producto más caro. (Utilice solamente las cláusulas ORDER BY y LIMIT)
```sql
SELECT nombre, precio FROM producto ORDER BY precio DESC LIMIT 1;

```
2.20. Lista el nombre de todos los productos del fabricante cuyo identificador de fabricante es igual a 2.
```sql
SELECT p.nombre FROM producto p JOIN fabricante f ON p.codigo_fabricante = f.codigo WHERE f.codigo = 2;

```
2.21. Lista el nombre de los productos que tienen un precio menor o igual a 120€.
```sql
SELECT nombre FROM producto WHERE precio <= 120;

```
2.22. Lista el nombre de los productos que tienen un precio mayor o igual a 400€.
```sql
SELECT nombre FROM producto WHERE precio >= 400;

```
2.23. Lista el nombre de los productos que no tienen un precio mayor o igual a 400€.
```sql
SELECT nombre FROM producto WHERE precio < 400;

```
2.24. Lista todos los productos que tengan un precio entre 80€ y 300€. Sin utilizar el operador BETWEEN.
```sql
SELECT nombre FROM producto WHERE precio > 80 AND precio < 300;

```
2.25. Lista todos los productos que tengan un precio entre 60€ y 200€. Utilizando el operador BETWEEN.
```sql
SELECT nombre FROM producto WHERE precio BETWEEN 60 AND 200;

```
2.26. Lista todos los productos que tengan un precio mayor que 200€ y que el identificador de fabricante sea igual a 6.
```sql
SELECT nombre FROM producto WHERE precio > 200 AND codigo_fabricante = 6;

```
2.27. Lista todos los productos donde el identificador de fabricante sea 1, 3 o 5. Sin utilizar el operador IN.
```sql
SELECT nombre FROM producto WHERE codigo_fabricante = 1 OR codigo_fabricante = 3 OR codigo_fabricante = 5;

```
2.28. Lista todos los productos donde el identificador de fabricante sea 1, 3 o 5. Utilizando el operador IN.
```sql
SELECT nombre FROM producto WHERE codigo_fabricante IN (1, 3, 5);

```
2.29. Lista el nombre y el precio de los productos en céntimos (Habrá que multiplicar por 100 el valor del precio). Cree un alias para la columna que contiene el precio que se llame céntimos.
```sql
SELECT nombre, precio * 100 AS céntimos FROM producto;

```
2.30. Lista los nombres de los fabricantes cuyo nombre empiece por la letra S.
```sql
SELECT nombre FROM fabricante WHERE nombre LIKE 'S%';

```
2.31. Lista los nombres de los fabricantes cuyo nombre termine por la vocal e.
```sql
SELECT nombre FROM fabricante WHERE nombre LIKE '%e';

```
2.32. Lista los nombres de los fabricantes cuyo nombre contenga el carácter w.
```sql
SELECT nombre FROM fabricante WHERE nombre LIKE '%w%';

```
2.33. Lista los nombres de los fabricantes cuyo nombre sea de 4 caracteres.
```sql
SELECT nombre FROM fabricante WHERE LENGTH(nombre) = 4;

```
2.34. Devuelve una lista con el nombre de todos los productos que contienen la cadena Portátil en el nombre.
```sql
SELECT nombre FROM producto WHERE nombre LIKE '%Portátil%';

```
2.35. Devuelve una lista con el nombre de todos los productos que contienen la cadena Monitor en el nombre y tienen un precio inferior a 215 €.
```sql
SELECT nombre FROM producto WHERE nombre LIKE '%Monitor%' AND precio < 215;

```

2.36. Lista el nombre y el precio de todos los productos que tengan un precio mayor o igual a 180€. Ordene el resultado en primer lugar por el precio (en orden descendente) y en segundo lugar por el nombre (en orden ascendente).
```sql
SELECT nombre, precio FROM producto WHERE precio >= 180 ORDER BY precio DESC, nombre ASC;

```