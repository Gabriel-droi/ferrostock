# FerroStock – Sistema de inventario para ferretería

**Examen práctico: Ciclo de vida de un proyecto informático**
**Equipo:** (escriban aquí los nombres de los 6 integrantes)
**Prototipo publicado:** `https://TU-USUARIO.github.io/ferrostock/`

---

## 1. Objetivo principal

**Nombre del proyecto:** FerroStock

**Problema:** Una ferretería lleva su inventario en cuadernos y hojas sueltas. Por eso no sabe cuánto stock tiene realmente, se queda sin productos de mucha venta, compra de más otros y pierde tiempo buscando datos.

**Objetivo principal:** Desarrollar un sistema web de inventario que permita controlar productos, proveedores y movimientos de bodega, y avise cuando un producto necesita reposición.

**Objetivos específicos:**
1. Registrar y consultar productos con su precio, stock y stock mínimo.
2. Registrar entradas y salidas de bodega y actualizar el stock automáticamente.
3. Mantener un directorio de proveedores asociado a cada producto.
4. Mostrar alertas de stock bajo y un resumen del inventario.

**Alcance inicial:**
- Incluye: módulos de Inicio (resumen), Productos, Proveedores y Movimientos, con datos ficticios.
- No incluye (primera versión): base de datos real, inicio de sesión, facturación, reportes en PDF ni conexión con tienda en línea.

---

## 2. Análisis funcional

**Usuarios del sistema**
| Usuario | Qué hace |
|---|---|
| Administrador / dueño | Consulta el resumen, administra productos y proveedores |
| Bodeguero | Registra entradas y salidas de mercancía |
| Vendedor | Consulta disponibilidad y precios |

**Necesidades principales:** saber cuánto hay de cada producto, evitar quedarse sin stock, saber a quién pedirle cada producto y tener un historial de lo que entra y sale.

**Requisitos funcionales**
| ID | Requisito |
|---|---|
| RF1 | El sistema permite registrar un producto (código, nombre, precio, stock, mínimo, proveedor). |
| RF2 | El sistema permite buscar productos por código o nombre. |
| RF3 | El sistema permite registrar entradas y salidas y actualiza el stock. |
| RF4 | El sistema impide una salida mayor al stock disponible. |
| RF5 | El sistema muestra una lista de productos con stock bajo en la página de inicio. |
| RF6 | El sistema permite registrar y consultar proveedores. |
| RF7 | El sistema muestra el historial de movimientos. |

**Requisitos no funcionales**
| ID | Requisito |
|---|---|
| RNF1 | Usabilidad: un empleado nuevo debe aprender a usarlo en menos de 15 minutos. |
| RNF2 | Compatibilidad: funciona en Chrome, Firefox y Edge actuales. |
| RNF3 | Diseño adaptable: se ve bien en computadora y celular. |
| RNF4 | Rendimiento: cada pantalla carga en menos de 2 segundos. |
| RNF5 | Disponibilidad: accesible desde internet (GitHub Pages) sin instalación. |
| RNF6 | Mantenibilidad: código organizado y versionado en GitHub. |

---

## 3. Planificación

**Responsabilidades**
| Integrante | Responsabilidad |
|---|---|
| 1 – _nombre_ | Líder / coordinación |
| 2 – _nombre_ | Análisis funcional |
| 3 – _nombre_ | Requisitos y documentación |
| 4 – _nombre_ | Diseño UI |
| 5 – _nombre_ | Desarrollo |
| 6 – _nombre_ | GitHub / integración y pruebas |

**Calendario de trabajo**
| Semana | Etapa | Resultado |
|---|---|---|
| 1 | Análisis | Requisitos aprobados |
| 2 | Diseño | Pantallas y navegación definidas |
| 3–4 | Desarrollo | Módulos funcionando |
| 5 | Pruebas | Errores corregidos |
| 6 | Publicación | Prototipo en GitHub Pages |

---

## 4. Diseño detallado

**Arquitectura propuesta:** aplicación web de tres capas.
- Presentación: HTML, CSS y JavaScript (interfaz que ve el usuario).
- Lógica: JavaScript en el navegador (prototipo); en la versión final, una API REST.
- Datos: arreglos en memoria (prototipo); en la versión final, base de datos relacional.

```
Usuario → Navegador (HTML/CSS/JS) → API REST (futuro) → Base de datos (futuro)
```

**Tecnologías**
| Capa | Prototipo | Versión final propuesta |
|---|---|---|
| Interfaz | HTML5, CSS3, JavaScript | Igual |
| Servidor | – | Node.js + Express |
| Datos | Datos ficticios | MySQL o PostgreSQL |
| Control de versiones y hosting | Git, GitHub, GitHub Pages | Igual / servidor propio |

**Módulos:** Inicio (resumen y alertas), Productos, Proveedores, Movimientos.

**Navegación:** menú lateral fijo con cuatro enlaces: Inicio → Productos → Proveedores → Movimientos. Desde cualquier pantalla se puede ir a otra con un clic.

**Pantallas principales**
```
INICIO                         PRODUCTOS
[4 indicadores]                [Formulario nuevo producto]
[Tabla: reponer pronto]        [Buscador]
                               [Tabla: código|producto|precio|stock|estado]

PROVEEDORES                    MOVIMIENTOS
[Formulario proveedor]         [Formulario: producto|tipo|cantidad]
[Tabla de proveedores]         [Tabla: historial]
```

---

## 5. Ejecución

Prototipo funcional en `index.html` con:
- Página de inicio con resumen del inventario.
- Menú lateral de navegación.
- 3 módulos principales (Productos, Proveedores, Movimientos), más el resumen de Inicio.
- Datos ficticios precargados.
- Formularios y tablas representativas que sí funcionan (en memoria, sin base de datos).

---

## 6. Seguimiento y control

Pruebas realizadas durante el desarrollo:

| Prueba | Resultado esperado | Estado |
|---|---|---|
| Navegar por los 4 enlaces del menú | Cambia de sección sin recargar | Correcto |
| Registrar un producto nuevo | Aparece en la tabla y en el resumen | Correcto |
| Registrar un código repetido | Muestra mensaje de error | Correcto |
| Registrar una salida mayor al stock | Muestra error y no cambia el stock | Correcto |
| Registrar una entrada | Suma al stock y queda en el historial | Correcto |
| Abrir en un celular | Se adapta a pantalla pequeña | Correcto |

---

## 7. Aceptación

**¿El prototipo demuestra la solución planteada?** Sí. Permite ver el estado del inventario, registrar productos, proveedores y movimientos, y alerta cuando el stock es bajo, que era el problema principal del cliente.

**Requisitos demostrables con el prototipo**
| Requisito | Cómo se demuestra |
|---|---|
| RF1 | Módulo Productos → "Guardar producto" |
| RF2 | Módulo Productos → buscador |
| RF3 | Módulo Movimientos → registrar entrada o salida y ver el stock cambiar |
| RF4 | Registrar una salida mayor al stock y ver el mensaje de error |
| RF5 | Página de inicio → tabla "Reponer pronto" |
| RNF3 | Abrir la URL en el celular o reducir la ventana |

---

## 8. Cierre

- Código subido a GitHub: repositorio `ferrostock`.
- Publicado con GitHub Pages.
- URL del prototipo: `https://TU-USUARIO.github.io/ferrostock/`

## 9. Mantenimiento (propuesta futura)

Conectar una base de datos real, agregar inicio de sesión con roles, reportes en PDF/Excel, avisos por correo cuando el stock sea bajo y copias de seguridad periódicas.
