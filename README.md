## 🧠 Guía básica sobre Django: CRUD, estructura y patrones
Este documento responde de forma clara y sencilla a preguntas comunes sobre cómo funciona Django, sus patrones de arquitectura, y cómo estructurar un proyecto web con CRUD.


### 1. ¿Qué es un CRUD y cuál es su propósito en el desarrollo de aplicaciones web?

```text
CRUD es un acrónimo que describe las acciones básicas que puedes realizar con los datos en una aplicación web o base de datos.
C-->  ➕ Create -> Crear
R-->  🔍 Read   -> Leer
U-->  ♻️ Update -> Actualizar
D-->  ❌ Delete -> Eliminar

```

📱 Ejemplo: Gestión de publicaciones en una red social

- ➕ Crear: Publicar un nuevo post con texto, imagen o video.
- 🔎 Leer: Ver el feed, los likes, comentarios y publicaciones de otros usuarios.
- ♻️ Actualizar: Editar el contenido de una publicación ya hecha, como cambiar el texto.
- ❌  Eliminar: Borrar un post que ya no deseas mostrar públicamente.






### 2. ¿Qué son los patrones de arquitectura en desarrollo de software?
   
 ```text
Imagina que vas a construir una casa 🏠. Los patrones de arquitectura son como los planos:
te ayudan a organizar las piezas de una aplicación.

No son bloques de código, sino formas probadas de estructurar una app que:
- facilitan el mantenimiento
- hacen el código más limpio
- permiten crecer sin romper todo

Un patrón de arquitectura define:
- La estructura del sistema
- Cómo se comunican los componentes
- Qué responsabilidades tiene cada parte
```
🔧 Se utilizan para mejorar la escalabilidad, mantenibilidad, modularidad y reutilización del software.



   
#### 2.1 ¿Qué es el patrón MVC (Modelo–Vista–Controlador)?
```text
El patrón MVC (Modelo–Vista–Controlador) es una arquitectura, es una forma de dividir el proyecto en 3 partes bien separadas:

- Modelo: gestiona los datos (como los productos de una tienda)
- Vista: lo que el usuario ve en pantalla (HTML, CSS)
- Controlador: maneja la lógica y las acciones (qué pasa cuando haces clic)

🔍 Esto ayuda a que cada parte tenga su función y sea más fácil de modificar sin romper el resto.
```

#### 2.2 ¿Qué es el patrón MVT (Modelo–Vista–Template)?
```text

- En MVT, el controlador lo maneja Django automáticamente.
  - el modelo (estructura de datos),
  - la vista (lógica que responde),
  - el template (el HTML que se muestra).

```
⚠️ Nota: En Django, "vista" no significa lo que ves en pantalla. Es una **función en `views.py` que contiene la lógica del servidor**.


#### 2.3  Diferencias entre MVC y MVT.
```text
- En MVC, tú escribes el controlador.
- En MVT, Django lo hace por ti.
- En MVT, la "vista" es la lógica (no la interfaz), y el template es la presentación visual.

🔎 Django utiliza el patrón MVT:
- Tú defines el Modelo, la Vista (función lógica) y el Template.
- Django se encarga del enrutamiento y de actuar como controlador.

```
#### 2.4 ¿Cuál de estos dos patrones se usa en Django?
```bash
Django sigue el patrón MVT, una variante de MVC donde el framework asume el papel del controlador
y tú te concentras en el modelo, la lógica de vista y la presentación.
```
### 3. ¿Cómo se estructura un proyecto en Django? 
Para trabajar de forma ordenada y escalable, Django propone una estructura clara entre el proyecto principal y sus aplicaciones internas.

## 🧱 Estructura General de un proyecto Django
```text

Un proyecto Django se divide en:

1. Proyecto principal: configuración global del sitio.
2. Aplicaciones (apps): módulos independientes (usuarios, blog, tienda, etc.).
```

| 📂 Archivo / Carpeta      | 📌 Descripción                                     |
| ------------------------- | -------------------------------------------------- |
| `manage.py`               | Script principal para ejecutar comandos Django     |
| `mi_proyecto/`            | Configuración global del proyecto                  |
| ├── `settings.py`         | Ajustes generales (base de datos, apps, etc.)      |
| ├── `urls.py`             | Rutas del sitio web                                |
| └── `wsgi.py` / `asgi.py` | Entrada para servidores web                        |
| `mi_app/`                 | Módulo de una funcionalidad específica             |
| ├── `models.py`           | Estructura de datos (clases -> tablas)             |
| ├── `views.py`            | Lógica de respuesta a solicitudes                  |
| ├── `urls.py`             | Rutas específicas de la app                        |
| ├── `templates/`          | HTML con lógica visual                             |
| └── `migrations/`         | Cambios estructurales aplicados a la base de datos |







#### 3.1 ¿Para qué se usa el signo "{% %}" en los templates?

```text

✅ Se usa para lógica de plantilla como bucles y condicionales:

{% for libro in libros %}
  <li>{{ libro.titulo }}</li>
{% endfor %}

```
+ {% ... %} → lógica

+ {{ ... }} → mostrar datos


### 4. ¿Cuál es el flujo de datos entre un formulario HTML y la base de datos en Django?
```text

   🔄 Formulario → Base de datos

1. 🧑‍💻 Usuario llena formulario
2. ⬇️ El navegador envía POST al servidor
3. 🔀 Django busca coincidencias en `urls.py`
4. 🧠 Se ejecuta la función en `views.py`
5. 🗃️ Los datos se guardan en la base de datos vía `models.py`
6. ✅ Se responde con confirmación o redirección

✅ Así Django procesa los datos:
- El usuario envía información
- Django la interpreta y ejecuta la lógica
- Si todo está bien, guarda los datos y responde


```
Este flujo permite manejar formularios fácilmente en Django.


### 5  ¿Qué herramientas o comandos ofrece Django para facilitar el desarrollo de un CRUD, para qué es cada una? 
#### (Por ejemplo: startapp, makemigrations, migrate, runserver, ModelForm, admin, etc.)


| 🧰 Comando / Herramienta | ¿Para qué sirve?                                            |
| ------------------------ | ----------------------------------------------------------- |
| `startapp`               | Crea una nueva app dentro del proyecto                      |
| `makemigrations`         | Detecta cambios en los modelos y crea archivos de migración |
| `migrate`                | Aplica las migraciones a la base de datos                   |
| `runserver`              | Inicia el servidor local para pruebas                       |
| `createsuperuser`        | Crea un usuario administrador                               |
| `ModelForm`              | Genera formularios automáticamente desde modelos,           |
| `admin`                  | Interfaz administrativa web para gestionar los modelos      |

### 6. ¿Cómo funciona el Admin de Django?
```text
El Admin de Django es como una “oficina virtual” preconstruida. Te permite gestionar fácilmente los datos de tu sitio web
sin tener que programar interfaces desde cero.

🛠️ Funciona así:
- Detecta tus modelos si los registras.
- Muestra una interfaz CRUD para ellos.
- Controla el acceso por usuario/rol.
- Puedes personalizar filtros, campos, búsqueda, etc.

```

👉 Accedes desde /admin en el navegador.

🎯 ¿Por qué es útil?

Te ahorra horas de desarrollo.

Es seguro, extensible y muy práctico para proyectos reales.
