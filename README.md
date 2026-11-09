<p align="center">
  <img src="public/assets/img/logo-enlaza.png" alt="Enlaza logo" width="120">
</p>

<h1 align="center">Enlaza</h1>

<p align="center">
  A web platform that connects volunteers with non-profit organizations.<br>
  <i>Conecta. Participa. Transforma.</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/PHP-777BB4?logo=php&logoColor=white" alt="PHP">
  <img src="https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=white" alt="MySQL">
  <img src="https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white" alt="HTML5">
  <img src="https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white" alt="CSS3">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black" alt="JavaScript">
</p>

---

## Features

- [x] Sign up and log in (volunteer or organization)
- [ ] Volunteer and organization profiles
- [ ] Publish, edit and close opportunities
- [ ] Search and filter opportunities
- [ ] Enroll in opportunities and manage enrollments (accept / reject)
- [ ] Recommendations based on skills, interests and location

## Tech stack

| Layer | Technology |
| --- | --- |
| Backend | Plain PHP with PDO |
| Database | MySQL / MariaDB |
| Frontend | HTML, CSS and vanilla JavaScript |
| Local server | XAMPP or Laragon |

## How to run it

1. Copy the project into `htdocs` (XAMPP) or `www` (Laragon).
2. Import the database:

   ```bash
   mysql -u root -p < database/schema.sql
   mysql -u root -p < database/migration_001.sql
   mysql -u root -p < database/seeds.sql
   ```

3. If your MySQL has a user or password, change `DB_USER` and `DB_PASS` in `config/config.php`.
4. Open `http://localhost/<project-folder>/public/`.

> [!IMPORTANT]
> Run the SQL files in this order. `seeds.sql` uses columns that `migration_001.sql` creates.

> [!WARNING]
> `seeds.sql` deletes all the data in the tables before adding the demo data. Don't run it on data you want to keep.

## Test accounts

All accounts use the password `enlaza123`.

| Role | Email |
| --- | --- |
| Organization | `contacto@verdenorte.org` |
| Volunteer | `paulina.rojas@correo.com` |

<details>
<summary>See all accounts</summary>

**Organizations**

| Email | Organization |
| --- | --- |
| `contacto@verdenorte.org` | Fundación Verde Norte |
| `info@aprenderjuntos.org` | Asociación Aprender Juntos |
| `sancarlos@cruzroja.org` | Cruz Roja — sede local |
| `cultura@zarcero.org` | Casa de la Cultura Zarcero |

**Volunteers**

| Email | Name |
| --- | --- |
| `paulina.rojas@correo.com` | Paulina Rojas |
| `ana.rodriguez@correo.com` | Ana Rodríguez |
| `luis.vargas@correo.com` | Luis Vargas |
| `kimberly.solano@correo.com` | Kimberly Solano |
| `josue.alfaro@correo.com` | Josué Alfaro |
| `melany.rojas@correo.com` | Melany Rojas |
| `diego.cespedes@correo.com` | Diego Céspedes |
| `fabiola.quesada@correo.com` | Fabiola Quesada |

</details>

## Project structure

<details>
<summary>See project structure</summary>

```
public/             → index.php (router) and assets (css, js, img)
app/
  controllers/      → one controller per module
  models/           → one model per table (PDO)
  views/            → .php pages and partials
  helpers/          → helper functions for the views
config/             → database connection and constants
database/           → schema, migrations and demo data
design-reference/   → visual prototypes (they don't run)
```

</details>

## Author

**Paulina Rojas** — [@paulina-rc](https://github.com/paulina-rc)

## License

MIT License. See [LICENSE](LICENSE) for details.

