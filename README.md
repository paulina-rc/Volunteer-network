# Enlaza — Plataforma de voluntariado

Plataforma web que conecta voluntarios con organizaciones sin fines de lucro.
Proyecto TIC — Benemérito Colegio Agropecuario de San Carlos.

Stack: **PHP nativo (PDO) + MySQL/MariaDB + HTML/CSS/JS vanilla**, sin frameworks.

El contexto completo del proyecto (identidad visual, convenciones de nombres,
reglas de negocio y plan de desarrollo) está en [`CLAUDE.md`](CLAUDE.md).

## Instalación local (XAMPP / Laragon)

1. Copiá esta carpeta dentro de `htdocs` (XAMPP) o `www` (Laragon), por ejemplo como `enlaza/`.
2. Importá los **tres** archivos SQL **en este orden**:

   ```
   mysql -u root -p < database/schema.sql
   mysql -u root -p < database/migration_001.sql
   mysql -u root -p < database/seeds.sql
   ```

   - `schema.sql` — crea la base `enlaza` y las 10 tablas.
   - `migration_001.sql` — agrega lo que las pantallas necesitan y el esquema base
     todavía no tenía: `opportunities.requirements`, el estado `draft` en
     `opportunities.status`, el estado `completed` en `enrollments.status`,
     `organizations.category_id` y `organizations.founded_year`, más los índices
     de búsqueda.
   - `seeds.sql` — datos de demo. **Hace `TRUNCATE` de todas las tablas antes de
     insertar**, así que no lo corrás sobre datos que quieras conservar.

   El orden importa: `seeds.sql` inserta en columnas que crea `migration_001.sql`,
   así que saltarse la migración hace fallar la importación.

3. Revisá `config/config.php` y ajustá `DB_USER` / `DB_PASS` si tu MySQL local los
   requiere. **No hace falta tocar `BASE_URL`**: se calcula solo a partir de la URL
   del pedido, así que la carpeta puede llamarse como sea, incluso con espacios
   (`Red de voluntariados`), y las rutas de CSS, JS e imágenes se arman bien.
4. Configurá el servidor para que el **document root** apunte a la carpeta `public/`,
   o accedé directamente a la carpeta dentro de `htdocs`, por ejemplo
   `http://localhost/Red%20de%20voluntariados/public/`.

## Cuentas de prueba

Todas las cuentas del seed usan la contraseña **`enlaza123`**.

### Organizaciones

| Correo | Organización |
|---|---|
| `contacto@verdenorte.org` | Fundación Verde Norte |
| `info@aprenderjuntos.org` | Asociación Aprender Juntos |
| `sancarlos@cruzroja.org` | Cruz Roja — sede local |
| `cultura@zarcero.org` | Casa de la Cultura Zarcero |

### Voluntarios

| Correo | Nombre |
|---|---|
| `paulina.rojas@correo.com` | Paulina Rojas |
| `ana.rodriguez@correo.com` | Ana Rodríguez |
| `luis.vargas@correo.com` | Luis Vargas |
| `kimberly.solano@correo.com` | Kimberly Solano |
| `josue.alfaro@correo.com` | Josué Alfaro |
| `melany.rojas@correo.com` | Melany Rojas |
| `diego.cespedes@correo.com` | Diego Céspedes |
| `fabiola.quesada@correo.com` | Fabiola Quesada |

El seed trae además 5 categorías, 12 habilidades, 13 oportunidades (10 activas,
2 cerradas, 1 borrador) y 28 inscripciones en estados mezclados.

## Estructura

```
/public              → index.php (entrada y router), /assets (css, js, img)
/app
  /controllers       → una clase por módulo
  /models            → una clase por entidad, PDO
  /views             → plantillas .php de cada pantalla + /partials
  /helpers           → functions.php (helpers de vista), view.php
/config              → conexión a BD, constantes globales
/database            → schema.sql, migration_001.sql, seeds.sql
/design-reference    → prototipos *.dc.html (referencia visual, no se ejecutan)
```




