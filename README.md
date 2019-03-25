## Entrega Exercici 1- RA1 - Objectes, classes i herència a Postgres

**L'objectiu d'aquest exercici és conèixer i practicar el concepte de classes, objectes i herències en el SGBD Postgres.**

**Per això:**

**Llegir: https://www.postgresql.org/docs/current/static/ddl-inherit.html**

**( assegurar de llegir la documentació en la versió de postgres que vosaltres utilitzeu)**

1. **Seguiu l'exemple explicat: creant la taula Cities i Capitals.  Proveu de fer insercions en ambdues taules i veure els resultats.**

   Script de creacio i eliminacio si existeixen les taules per crearles. 

```sql
DROP TABLE IF EXISTS capitals;
DROP TABLE IF EXISTS cities;

CREATE TABLE cities (
    name            text,
    population      float,
    altitude        int     -- in feet
);

CREATE TABLE capitals (
    state           char(2)
) INHERITS (cities);
```



2. **Per què creieu que s'utilitza el tableoid ? i el pg_class ?**

*tableoid*

TABLEOID és un valor sencer d'increment automàtic, únic dins d'una base de dades PostgreSQL (no només una taula) que es pot assignar automàticament a cada fila d'una taula.

Tot i que OID es pot utilitzar com a clau primària d’identitat d'una columna(increment automàtic), es recomana utilitzar el tipus de dades SERIAL.

*pg_class*

El catàleg pg_class cataloga les taules i la majoria de totes les altres que tinguin columnes o siguin similars a una taula. Inclou índexs (però també pg_index), seqüències, vistes, tipus compostos i alguns tipus de relació especial; vegeu relkind. A continuació, quan ens referim a tots aquests objectes, parlem de "relacions". No totes les columnes tenen sentit per a tots els tipus de relació.

3. **Al llegir la documentació. Penseu que es pot utilitzar l'herència múltiple en Postgres ? Fiqueu algun exemple**



4. **Identifiqueu algunes limitacions de l'herència en Postgres.  Estudieu com es propaguen les foreign keys o els canvis de taules etc..  d'una classe "pare" o superclasse a les seves classes "filles". Podeu  consultar per les instruccions:`SELECT`, `UPDATE`, `DELETE`, `ALTER TABLE`,  `ALTER TABLE ... RENAME, vauum, reindex`).**