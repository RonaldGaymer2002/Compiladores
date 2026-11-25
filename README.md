<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=200&section=header&text=Compilador%20GoX&fontSize=50&fontColor=fff&animation=fadeIn&desc=De%20C%C3%B3digo%20Fuente%20a%20M%C3%A1quina%20de%20Pila%20%7C%20Compilador%20Educativo&descSize=16&descAlignY=65"/>
</div>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10-3776AB?logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Parser-LL(1)-0066FF"/>
  <img src="https://img.shields.io/badge/Pipeline-AST--IR-FF6F00"/>
  <img src="https://img.shields.io/badge/Licencia-MIT-yellow"/>
</p>

<p align="center">
  <a href="#-integrantes">Integrantes</a> •
  <a href="#-descripci%C3%B3n-general">Descripción</a> •
  <a href="#-pipeline-de-compilaci%C3%B3n">Pipeline</a> •
  <a href="#-uso-y-ejecuci%C3%B3n">Uso</a> •
  <a href="#-caracter%C3%ADsticas-del-lenguaje">Características</a> •
  <a href="#-documentaci%C3%B3n">Documentación</a>
</p>

---

## 👥 Integrantes — Grupo #3

- **Jhon Freddy Villca Isla**
- **David Alexander Terceros Jordan**
- **Ronald Augusto Rodriguez Serrano**

*Materia: Compiladores — UTEPSA*

---

## 🎯 Descripción General

Compilador multi-etapa desarrollado desde cero en Python para el lenguaje **GoX**. Transforma el código fuente mediante análisis léxico, análisis sintáctico por descenso recursivo (LL(1)), análisis semántico con verificación de tipos y ámbitos, generación de código intermedio (IR de tres direcciones) y ejecución en una máquina virtual de pila (*Stack Machine*).

> 📚 Proyecto educativo que demuestra el pipeline completo de compilación: desde el texto en bruto hasta la ejecución en memoria.

---

## 🔧 Pipeline de Compilación

```
Código Fuente (.gox)
        │
        ▼
┌─────────────────────────┐
│   ① Lexer (Escáner)     │  Tokenización: código → [Token, Token, ...]
└───────────┬─────────────┘
            ▼
┌─────────────────────────┐
│   ② Parser (LL(1))      │  Construcción del AST desde el flujo de tokens
└───────────┬─────────────┘
            ▼
┌─────────────────────────┐
│   ③ Analizador          │  Chequeo de tipos, resolución de ámbitos
│      Semántico          │  y validación de la tabla de símbolos
└───────────┬─────────────┘
            ▼
┌─────────────────────────┐
│   ④ Generador de IR     │  Código intermedio (tres direcciones / cuádruplos)
└───────────┬─────────────┘
            ▼
┌─────────────────────────┐
│   ⑤ Máquina de Pila     │  Ejecución del IR en máquina virtual personalizada
└─────────────────────────┘
            │
            ▼
    Salida del Programa
```

---

## 🚀 Uso y Ejecución

### 1. Ejecutar el Compilador Completo y la Máquina Virtual

Para compilar y ejecutar un archivo fuente `.gox` de extremo a extremo:

```powershell
# En Windows (PowerShell)
$env:PYTHONPATH="Final"
python Final\StackMachine.py demo.gox
```

### 2. Ejecutar la Interfaz Gráfica (Tkinter)

Abre la interfaz de escritorio para seleccionar y procesar archivos `.gox`:

```bash
python Documentation/src/main.py
```

### 3. Servidor Web de Documentación Interactiva

Para explorar la documentación web interactiva de cada módulo con Tailwind CSS y Markdown:

```bash
python -m http.server 8000 -d Documentation
```
Luego abre tu navegador en [http://localhost:8000](http://localhost:8000).

---

## ✨ Características del Lenguaje GoX

Ejemplo de sintaxis soportada:

```go
// Declaración de variables y tipos
var x int = 10;
var total int = 0;

// Estructuras de control
if (x >= 5) {
    print x;
} else {
    print 0;
}

// Bucles
while (x > 0) {
    total = total + x;
    x = x - 1;
}

print total;
```

### Tipos de Tokens y Operadores

| Categoría | Ejemplos |
|:----------|:---------|
| **Palabras Clave** | `var`, `const`, `func`, `if`, `else`, `while`, `return`, `break`, `continue`, `print`, `import` |
| **Tipos de Datos** | `int`, `float`, `bool`, `string`, `char` |
| **Operadores** | `+`, `-`, `*`, `/`, `%`, `<=`, `>=`, `==`, `!=`, `<`, `>`, `&&`, `\|\|`, `!` |
| **Literales** | Enteros, flotantes, cadenas de texto, caracteres, booleanos (`true`, `false`) |
| **Comentarios** | De una sola línea (`//`) y multilínea (`/* ... */`) |

---

## 📂 Estructura del Proyecto

```
python-compiler/
├── Final/                     # Implementación consolidada del compilador
│   ├── Lexer.py               # Etapa 1: Análisis Léxico
│   ├── Parser.py              # Etapa 2: Análisis Sintáctico (AST)
│   ├── Nodes_AST.py           # Definición de nodos del AST
│   ├── SymbolTable.py         # Tabla de símbolos y alcances
│   ├── SemanticAnalyzer.py    # Etapa 3: Análisis Semántico y Tipos
│   ├── Types.py               # Sistema de tipos
│   ├── IRCodeGenerator.py     # Etapa 4: Generación de Código Intermedio
│   ├── StackMachine.py        # Etapa 5: Máquina Virtual de Pila
│   ├── AST_to_JSON.py         # Serializador del AST a formato JSON
│   ├── Error.py               # Gestor centralizado de errores
│   └── Compilador.md          # Especificación técnica detallada
├── Documentation/             # Documentación interactiva
│   ├── index.html             # Visor web de documentación
│   ├── Markdown/              # Documentos explicativos por fase
│   └── src/                   # Versión funcional integrada con GUI Tkinter
├── project/                   # Fases de desarrollo iterativo (v1, v2, v3, v4)
├── demo.gox                   # Script de demostración (cálculo de factorial)
├── ejemplo.gox                # Script básico de prueba
└── README.md                  # Este documento
```

---

## 📚 Módulos del Compilador

- **Lexer**: Especificación léxica basada en expresiones regulares, manejo de líneas y columnas, y reporte de caracteres no reconocidos.
- **Parser**: Gramática descendente recursiva LL(1), construcción formal de nodos del AST y recuperación básica ante fallos.
- **Analizador Semántico**: Control jerárquico de ámbitos (scopes), verificación de compatibilidad de tipos en expresiones y unicidad de identificadores.
- **Generador de IR**: Emisión de código intermedio de tres direcciones (`CONSTI`, `ADDI`, `GLOBAL_SET`, etc.) y simplificaciones lógicas.
- **Stack Machine**: Intérprete de instrucciones basado en una pila LIFO, con gestión de memoria y llamadas a funciones.

---

## 📜 Licencia

MIT — Consulta el archivo [LICENSE](LICENSE) para más detalles.

---

<p align="center">
  <i>Proyecto Académico — Compiladores, UTEPSA</i>
</p>
