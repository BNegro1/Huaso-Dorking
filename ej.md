# Ejemplos y Temáticas de Google Dorking (Chilean Edition)

## Definiciones Clave
- **Google Dorking**: Técnica para explotar la potencia de búsqueda de Google usando operadores avanzados. No es hacking, es sacar ventaja de la desorganización digital del mundo.
- **OSINT (Open Source Intelligence)**: Recolectar información de fuentes públicas como redes sociales, foros, y repositorios.
- **Keywords**: Palabras que actúan como imanes para datos sensibles (confidencial, backup, contraseña, interno, secreto).

## Operadores Básicos con Ejemplos Chilenos
| Operador | Uso | Ejemplo |
|----------|-----|---------|
| `site:` | Buscar en un dominio específico | `site:registrocivil.cl "padrón electoral"` |
| `filetype:` | Filtrar por tipo de archivo | `filetype:csv "rut, nombre, dirección"` |
| `intitle:` | Buscar palabras en el título | `intitle:"Dashboard" "admin" site:cl` |
| `inurl:` | Buscar palabras en la URL | `inurl:/wp-content/uploads site:cl` |
| `-` | Excluir términos | `"contrato" -"modelo" site:gob.cl` |

## Recetas de Búsqueda Prácticas
1. **Documentos Internos de Empresas Chilenas**:
   ```
   site:cl "Confidencial" (filetype:pdf OR filetype:docx) 2023
   ```
   - Resultados esperados: Informes financieros, contratos laborales, estrategias comerciales.

2. **Directorios Expuestos en Universidades**:
   ```
   intitle:"Index of" "/documentos" site:uchile.cl
   ```
   - Resultados esperados: Tesis, guías docentes, exámenes resueltos.

3. **Credenciales en Repositorios GitHub**:
   ```
   "DB_PASSWORD" "localhost" site:github.com
   ```
   - Resultados esperados: Accesos a bases de datos de startups chilenas.

## Herramientas Complementarias
1. **Google Hacking Database (GHDB)**: Repositorio de consultas de Google Dorking.
2. **Shodan**: Buscador de dispositivos IoT. Ejemplo: `country:CL port:22`
3. **Wayback Machine**: Recupera archivos eliminados de sitios web.

## Errores Comunes
- **Usar operadores sin contexto**:
  ```
  # MAL: filetype:pdf site:cl
  # BIEN: filetype:pdf "informe tributario" site:serviciodeimpuestosinternos.cl
  ```
- **Ignorar la caché de Google**:
  ```
  cache:twitter.com "mensaje borrado por la corte"
  ```

## Consideraciones Legales
- **Ley 19.223 (Delitos Informáticos)**: Penas de hasta 5 años por acceso no autorizado.
- **Ley 19.628 (Protección de Datos)**: Multas por filtrar información personal.
- **Regla de Oro**: Si encuentras algo ilegal, repórtalo y sigue de largo.

## Búsqueda Avanzada para Instituciones Públicas
```
site:gob.cl ("usuario" OR "contraseña") (filetype:xls OR filetype:txt)
```
- Resultados esperados: Planillas de usuarios/contraseñas de sistemas internos.

## Búsqueda en Google Drive
```
site:drive.google.com ("confidential" OR "internal" OR "restricted" OR "ssn" OR "social security number" OR "PII" OR "classified" OR "financial records" OR "passport number" OR "Orders" OR "Employee Details" OR "salary report" OR "performance review" OR "personal information" OR "client list" OR "HR" OR "payroll" OR "Home Address" OR "Marital Status" OR "internal use only" OR "do not share" OR "company confidential" OR "proprietary" OR "security clearance" OR "confidential report" OR "military orders" OR "deployment" OR "department of defense" OR "government document" OR "security clearance level" OR "defense orders" OR "intelligence report" OR "top secret" OR "sensitive data" OR "inurl:folders" OR "inurl:view" OR "restricted access" OR "private files" OR "inurl:\"id=\" intext:\"readonly\"" OR "usp=sharing" OR "mode=readonly" OR "filetype:pdf" OR "filetype:xlsx")
```
- Resultados esperados: Documentos confidenciales compartidos públicamente en Google Drive.
