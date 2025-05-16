# Tablas de salida

**Nota:** Utilizar ``load.sql`` para obtener la misma base de datos. Las salidas presentadas pueden tener errores.

### 1. Películas exhibidas en cines de ‘Avellaneda’ y que posean funciones en cines de ‘La Plata’

|       nombre       |
|:------------------:|
| Avengers: Endgame |
|       Soul        |
|      Tenet        |
|     Parasite      |

---

### 2. Películas exhibidas en funciones con menos de 30 espectadores

|  nombre   |
|:---------:|
|   Coco    |
| Frozen II |

---

### 3. Cines que exhiban todas las películas

|     nombre     |         direccion         |
|:--------------:|:-------------------------:|
| Cinemark Hoyts | Av. 51 543, La Plata      |

---

### 4. Cambio de nombre de la sala con código 10

**Antes:**

```sql
SELECT * FROM SALA WHERE codS = 10;
```

| cods |   nombres   |  descripcion   | capacidad | codc |
|:----:|:-----------:|:--------------:|:---------:|:----:|
|  10  | Sala Murray | Sala histórica |    90     |  5   |

**Actualización:**

```sql
UPDATE Sala
SET nombreS = 'Sala Darin'
WHERE codS = 10;
```

**Después:**

```sql
SELECT * FROM SALA WHERE codS = 10;
```

| cods |  nombres   |  descripcion   | capacidad | codc |
|:----:|:----------:|:--------------:|:---------:|:----:|
|  10  | Sala Darin | Sala histórica |    90     |  5   |

---

### 5. Cines donde se exhibe ‘007 Bond: Sin tiempo para morir’ o con funciones durante 2020

|        nombre        |             direccion              |
|:--------------------:|:----------------------------------:|
| Cine Lomas           | Calle España 123, Lomas de Zamora  |
| Cinemark Hoyts       | Av. 51 543, La Plata               |
| Multiplex Avellaneda | Calle Mitre 400, Avellaneda        |
| Showcase La Plata    | Calle 44 2045, La Plata            |

---

### 6. Películas exhibidas en ‘Cinemark Hoyts’ que no tienen funciones hoy allí

|       nombre       |                descripcion                |     genero      |
|:------------------:|:------------------------------------------:|:---------------:|
| Avengers: Endgame  | Última batalla de los Vengadores           | Acción          |
| Coco               | Historia de un niño mexicano y su familia  | Animación       |
| El Padrino         | Saga de crimen organizado                  | Drama           |
| Frozen II          | Aventura en tierras mágicas                | Animación       |
| Inside Out         | Las emociones de una niña                  | Animación       |
| Parasite           | Drama coreano sobre desigualdad            | Thriller        |
| Tenet              | Película de ciencia ficción y espionaje    | Ciencia Ficción |

---

### 7. Espectadores por película y cine durante 2020

|        nombre        |             nombre              | espectadores |
|:--------------------:|:-------------------------------:|:------------:|
| Cine Lomas           | 007 Bond: Sin tiempo para morir |      95      |
| Cinemark Hoyts       | Avengers: Endgame               |      35      |
| Cinemark Hoyts       | Coco                            |      25      |
| Cinemark Hoyts       | El Padrino                      |      50      |
| Cinemark Hoyts       | Frozen II                       |      60      |
| Cinemark Hoyts       | Parasite                        |      30      |
| Cinemark Hoyts       | Tenet                           |      45      |
| Multiplex Avellaneda | Parasite                        |      55      |
| Multiplex Avellaneda | Soul                            |      75      |
| Multiplex Avellaneda | Tenet                           |      40      |
| Showcase La Plata    | El Padrino                      |     100      |
| Showcase La Plata    | Parasite                        |      85      |

---

### 8. Eliminación del cine ‘Cine China Zorrilla’

**Cine eliminado:**

| codc |       nombre        |            direccion             |
|:----:|:-------------------:|:--------------------------------:|
|  5   | Cine China Zorrilla | Calle Uruguay 123, Montevideo   |

---

### 9. Exhibiciones por película durante 2020

|             nombre              | cant_exhibiciones |
|:------------------------------:|:-----------------:|
| 007 Bond: Sin tiempo para morir |         1         |
| Frozen II                       |         1         |
| Tenet                           |         2         |
| El Padrino                      |         2         |
| Soul                            |         1         |
| Parasite                        |         3         |
| Avengers: Endgame               |         1         |
| Coco                            |         1         |

---

### 10. Películas no exhibidas en 2020 en ningún cine de La Plata

| nombre |
|:------:|
| Minari |
