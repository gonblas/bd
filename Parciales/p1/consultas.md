# Consultas

1.
```sql
SELECT
  u_origen.nombreUsuario AS solicitante_usuario,
  u_origen.nombre AS solicitante_nombre,
  u_origen.apellido AS solicitante_apellido,
  u_destino.nombreUsuario AS receptor_usuario,
  u_destino.nombre AS receptor_nombre,
  u_destino.apellido AS receptor_apellido,
  s.fecha_solicitud
FROM Solicitudes s
JOIN Usuario u_origen ON s.nombreUsuarioSolicita = u_origen.nombreUsuario
JOIN Usuario u_destino ON s.nombreUsuarioRecibe = u_destino.nombreUsuario
WHERE s.fechaRechaza IS NOT NULL;
```


2.
```sql
SELECT u.nombreUsuario, u.correo, u.apellido, u.nombre
FROM Usuario u

EXCEPT

SELECT u.nombreUsuario, u.correo, u.apellido, u.nombre
FROM Usuario u
JOIN Publicacion p USING (nombreUsuario)
WHERE (p.tipoPub = 'Video') AND (p.fechaPub BETWEEN '2020-01-01' AND '2020-12-31');
```


3.
```sql
SELECT DISTINCT u.nombreUsuario, u.correo, u.apellido, u.nombre
FROM Usuario u
JOIN Comentario c USING (nombreUsuario)
WHERE EXTRACT(YEAR FROM c.fechaCom) = 2022
ORDER BY u.apellido, u.nombre

INTERSECT

SELECT DISTINCT u.nombreUsuario, u.correo, u.apellido, u.nombre
FROM Usuario u
JOIN Comentario c USING (nombreUsuario)
WHERE EXTRACT(YEAR FROM c.fechaCom) = EXTRACT(YEAR FROM CURRENT_DATE)
ORDER BY u.apellido, u.nombre;
```


4.
```sql
DELETE FROM Comentario WHERE idPublicacion = 50;
DELETE FROM Publicacion WHERE idPublicacion = 50; 
```


5.
```sql
SELECT u.nombreUsuario, COUNT(p.idPublicacion) AS cantPublicaciones
FROM Usuario u
LEFT JOIN Publicacion p ON (p.nombreUsuario = u.nombreUsuario)
GROUP BY u.nombreUsuario
ORDER BY cantPublicaciones DESC;
```


6.
```sql
SELECT u.nombreUsuario, COUNT(p.idPublicacion) AS cantPublicaciones
FROM Usuario u
JOIN Publicacion p ON p.nombreUsuario = u.nombreUsuario
GROUP BY u.nombreUsuario
HAVING COUNT(p.idPublicacion) = (
  SELECT COUNT(p2.idPublicacion) as cantPublicaciones2
  FROM Usuario u2
  JOIN Publicacion p2 ON p2.nombreUsuario = u2.nombreUsuario
  GROUP BY u2.nombreUsuario
  ORDER BY cantPublicaciones2 DESC
  LIMIT 1;
)
```


7.
```sql
SELECT p.fechaPub, p.titulo, p.tipoPub, u.correo, COUNT(c.idPublicacion) AS cant_comentarios
FROM Publicacion p
JOIN Usuario u USING (nombreUsuario)
JOIN Comentario c USING (idPublicacion)
WHERE p.titulo LIKE '%Publicidad%'
GROUP BY p.idPublicacion, p.fechaPub, p.titulo, p.tipoPub, u.correo
HAVING cant_comentarios > 1000;
```
