# 📖 APUNTES COMPLETOS - TÓPICOS DE PROGRAMACIÓN
## Unidad 1: Interfaces Gráficas con Java Swing

**Autor:** Apuntes Detallados con Análisis Línea por Línea  
**Fecha:** Febrero 2026  
**Nivel:** Intermedio  
**Total de Proyectos:** 15

---

## 📑 Tabla de Contenidos

### PARTE I: FUNDAMENTOS TEÓRICOS
1. [Introducción a Java Swing](#1-introduccion-a-java-swing)
2. [Conceptos Fundamentales](#2-conceptos-fundamentales)
3. [Componentes Básicos de Swing](#3-componentes-basicos-de-swing)
4. [Manejo de Eventos](#4-manejo-de-eventos)
5. [Layout Managers](#5-layout-managers)

### PARTE II: ANÁLISIS DETALLADO DE PROYECTOS

#### Nivel Básico - Primeros Pasos
6. [EjemploGUI_1 - Primera Ventana](#6-ejemplogui_1)
7. [ejemplogui - Ventana Básica](#7-ejemplogui)
8. [Test - Proyecto Base](#8-test)

#### Nivel Intermedio - Componentes Interactivos
9. [Bienvenida - Formulario con Radio Buttons](#9-bienvenida)
10. [CambiarTitulo - Manipulación de Propiedades](#10-cambiartitulo)
11. [CajasChequeo - Checkboxes](#11-cajaschequeo)
12. [Playback - Controles de Reproducción](#12-playback)
13. [ejerciciopractico - Práctica Guiada](#13-ejerciciopractico)

#### Nivel Avanzado - Aplicaciones Completas
14. [SegundaAplicacion - Suma de Valores](#14-segundaaplicacion)
15. [Practica3 - Calculadora de Operaciones Básicas](#15-practica3)
16. [operacionesbasicasboton - Calculadora con Botones](#16-operacionesbasicasboton)
17. [operacionesbascias2 - Calculadora Versión 2](#17-operacionesbascias2)
18. [Practica4 - Puntos de Fútbol](#18-practica4)
19. [practica5 - Conversor de Unidades](#19-practica5)
20. [practica8 - Tienda de Accesorios](#20-practica8)

### PARTE III: MEJORES PRÁCTICAS Y CONSEJOS
21. [Patrones de Diseño](#21-patrones-de-diseno)
22. [Errores Comunes y Soluciones](#22-errores-comunes)
23. [Ejercicios Propuestos](#23-ejercicios-propuestos)

---

# PARTE I: FUNDAMENTOS TEÓRICOS

---

## 1. Introducción a Java Swing

### 1.1 ¿Qué es Java Swing?

Java Swing es una biblioteca de componentes GUI (Graphical User Interface) que forma parte del JFC (Java Foundation Classes). Fue introducida para crear aplicaciones de escritorio con interfaces gráficas más modernas y flexibles que AWT (Abstract Window Toolkit).

**Características principales:**

- **Componentes ligeros (lightweight):** Los componentes Swing están escritos completamente en Java, lo que significa que no dependen de componentes nativos del sistema operativo
- **Independencia de plataforma:** El mismo código funciona en Windows, Linux y macOS sin modificaciones
- **Look and Feel personalizable:** Permite cambiar la apariencia de la aplicación para que se vea como Windows, Mac, Metal (Java), Nimbus, etc.
- **Arquitectura MVC:** Separación entre modelo (datos), vista (presentación) y controlador (lógica)
- **Rica variedad de componentes:** Botones, cajas de texto, tablas, árboles, menús, barras de herramientas, etc.

### 1.2 Paquetes Principales

```java
import javax.swing.*;      // Componentes Swing (JFrame, JButton, JTextField, etc.)
import java.awt.*;         // Abstract Window Toolkit (layouts, colores, fuentes, eventos gráficos)
import java.awt.event.*;   // Manejo de eventos (ActionListener, MouseListener, etc.)
```

**¿Por qué necesitamos estos tres paquetes?**
- `javax.swing.*` contiene todos los componentes visuales (botones, cajas de texto, etc.)
- `java.awt.*` contiene clases para layouts, colores, fuentes y dimensiones
- `java.awt.event.*` contiene las interfaces y clases para manejar eventos del usuario

### 1.3 Arquitectura de una Aplicación Swing

```
┌──────────────────────────────────────────────┐
│         JFrame (Ventana Principal)           │
│ ┌──────────────────────────────────────────┐ │
│ │    Content Pane (Panel de Contenido)     │ │
│ │  ┌──────────┐  ┌───────────────────┐    │ │
│ │  │ JButton  │  │     JLabel        │    │ │
│ │  │ "Click"  │  │ "Escribe tu nombre"│    │ │
│ │  └──────────┘  └───────────────────┘    │ │
│ │  ┌─────────────────────────────────┐    │ │
│ │  │      JTextField (entrada)       │    │ │
│ │  └─────────────────────────────────┘    │ │
│ └──────────────────────────────────────────┘ │
└──────────────────────────────────────────────┘
```

**Jerarquía de contenedores:**
1. **JFrame:** La ventana principal (nivel superior)
2. **Content Pane:** El panel donde se agregan los componentes
3. **Componentes:** Botones, etiquetas, cajas de texto, etc.

---

## 2. Conceptos Fundamentales

### 2.1 JFrame - La Ventana Principal

El `JFrame` es la ventana principal de cualquier aplicación Swing. Es el contenedor de nivel superior donde se colocan todos los demás componentes.

**Ejemplo básico:**

```java
import javax.swing.JFrame;

public class MiPrimeraVentana {
    public static void main(String[] args) {
        // Crear el JFrame
        JFrame ventana = new JFrame("Mi Primera Ventana");
        
        // Configurar tamaño (ancho, alto en píxeles)
        ventana.setSize(400, 300);
        
        // Hacer visible la ventana
        ventana.setVisible(true);
        
        // Definir qué pasa al cerrar la ventana
        ventana.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}
```

**Métodos importantes de JFrame:**

| Método | Descripción | Ejemplo |
|--------|-------------|---------|
| `setTitle(String)` | Establece el título de la ventana | `frame.setTitle("Mi App");` |
| `setSize(int width, int height)` | Define el tamaño en píxeles | `frame.setSize(800, 600);` |
| `setBounds(int x, int y, int width, int height)` | Posición y tamaño juntos | `frame.setBounds(100, 100, 800, 600);` |
| `setVisible(boolean)` | Muestra u oculta la ventana | `frame.setVisible(true);` |
| `setDefaultCloseOperation(int)` | Acción al cerrar | `frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);` |
| `setResizable(boolean)` | Permite/impide redimensionar | `frame.setResizable(false);` |
| `setLocationRelativeTo(Component)` | Centra la ventana | `frame.setLocationRelativeTo(null);` |
| `pack()` | Ajusta tamaño a componentes | `frame.pack();` |
| `setLayout(LayoutManager)` | Define el layout | `frame.setLayout(null);` |

**Constantes para setDefaultCloseOperation:**
- `JFrame.EXIT_ON_CLOSE` (3): Termina la aplicación completamente
- `JFrame.HIDE_ON_CLOSE` (1): Oculta la ventana pero la aplicación sigue corriendo
- `JFrame.DISPOSE_ON_CLOSE` (2): Libera recursos de la ventana
- `JFrame.DO_NOTHING_ON_CLOSE` (0): No hace nada al cerrar

**Dos formas de crear un JFrame:**

**Forma 1: Crear instancia directa**
```java
public class Main {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Ventana");
        frame.setSize(400, 300);
        frame.setVisible(true);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}
```

**Forma 2: Heredar de JFrame (MÁS COMÚN Y RECOMENDADA)**
```java
public class MiVentana extends JFrame {
    
    public MiVentana() {
        // Llamar al constructor del padre
        super("Mi Ventana");
        
        // Configurar la ventana
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null); // Centrar
        
        // Inicializar componentes
        inicializarComponentes();
    }
    
    private void inicializarComponentes() {
        // Aquí se agregan botones, etiquetas, etc.
    }
    
    public static void main(String[] args) {
        MiVentana ventana = new MiVentana();
        ventana.setVisible(true);
    }
}
```

**¿Por qué es mejor heredar de JFrame?**
- Mejor organización del código
- Facilita la reutilización
- Permite sobrescribir métodos si es necesario
- Es más orientado a objetos

---

## 3. Componentes Básicos de Swing

### 3.1 JLabel - Etiquetas de Texto

Las etiquetas (`JLabel`) se usan para mostrar texto o imágenes que NO son editables por el usuario.

**Sintaxis básica:**
```java
JLabel etiqueta = new JLabel("Texto a mostrar");
```

**Ejemplo completo:**
```java
// Crear etiqueta simple
JLabel lblNombre = new JLabel("Nombre:");

// Establecer posición y tamaño
lblNombre.setBounds(10, 10, 100, 25);
// setBounds(x, y, ancho, alto)
// x, y: coordenadas desde la esquina superior izquierda
// ancho, alto: dimensiones en píxeles

// Cambiar fuente
lblNombre.setFont(new Font("Arial", Font.BOLD, 14));
// Font(nombre, estilo, tamaño)
// Estilos: Font.PLAIN, Font.BOLD, Font.ITALIC

// Cambiar color de texto
lblNombre.setForeground(Color.BLUE);

// Cambiar color de fondo
lblNombre.setBackground(Color.YELLOW);
lblNombre.setOpaque(true); // Necesario para que se vea el fondo

// Alineación del texto
lblNombre.setHorizontalAlignment(SwingConstants.CENTER);
// Opciones: LEFT, CENTER, RIGHT

// Agregar al frame
frame.add(lblNombre);
```

**Métodos importantes de JLabel:**

| Método | Descripción |
|--------|-------------|
| `setText(String)` | Cambia el texto |
| `getText()` | Obtiene el texto actual |
| `setFont(Font)` | Cambia la fuente |
| `setForeground(Color)` | Color del texto |
| `setBackground(Color)` | Color de fondo |
| `setHorizontalAlignment(int)` | Alineación horizontal |
| `setIcon(Icon)` | Establece una imagen |

### 3.2 JTextField - Campos de Texto

Los campos de texto (`JTextField`) permiten al usuario ingresar texto en una sola línea.

**Sintaxis básica:**
```java
JTextField campoTexto = new JTextField();
// o con columnas predefinidas:
JTextField campoTexto = new JTextField(20); // 20 caracteres de ancho
```

**Ejemplo completo:**
```java
// Crear campo de texto
JTextField txtNombre = new JTextField();
txtNombre.setBounds(120, 10, 160, 25);

// Establecer texto inicial
txtNombre.setText("Escribe aquí");

// Obtener el texto ingresado
String texto = txtNombre.getText();

// Limpiar el campo
txtNombre.setText("");

// Hacer de solo lectura
txtNombre.setEditable(false);

// Cambiar fuente y color
txtNombre.setFont(new Font("Arial", Font.PLAIN, 12));
txtNombre.setForeground(Color.BLACK);

// Agregar al frame
frame.add(txtNombre);
```

**Métodos importantes de JTextField:**

| Método | Descripción |
|--------|-------------|
| `setText(String)` | Establece el texto |
| `getText()` | Obtiene el texto |
| `setEditable(boolean)` | Permite/impide editar |
| `setColumns(int)` | Establece ancho en columnas |
| `selectAll()` | Selecciona todo el texto |

### 3.3 JButton - Botones

Los botones (`JButton`) son componentes que el usuario puede presionar para ejecutar una acción.

**Sintaxis básica:**
```java
JButton boton = new JButton("Texto del Botón");
```

**Ejemplo completo:**
```java
// Crear botón
JButton btnAceptar = new JButton("Aceptar");
btnAceptar.setBounds(10, 80, 100, 30);

// Cambiar texto
btnAceptar.setText("OK");

// Cambiar colores
btnAceptar.setBackground(Color.GREEN);
btnAceptar.setForeground(Color.WHITE);

// Agregar al frame
frame.add(btnAceptar);

// Agregar funcionalidad (evento) - LO VEREMOS MÁS ADELANTE
btnAceptar.addActionListener(e -> {
    System.out.println("Botón presionado");
});
```

**Métodos importantes de JButton:**

| Método | Descripción |
|--------|-------------|
| `setText(String)` | Cambia el texto |
| `setEnabled(boolean)` | Activa/desactiva el botón |
| `addActionListener(ActionListener)` | Agrega evento al hacer clic |
| `setIcon(Icon)` | Agrega una imagen |

### 3.4 JRadioButton - Botones de Opción

Los radio buttons (`JRadioButton`) permiten seleccionar UNA opción de un grupo.

**IMPORTANTE:** Los radio buttons deben estar en un `ButtonGroup` para que solo uno esté seleccionado a la vez.

**Ejemplo completo:**
```java
// Crear los radio buttons
JRadioButton rbMasculino = new JRadioButton("Masculino");
JRadioButton rbFemenino = new JRadioButton("Femenino");
JRadioButton rbOtro = new JRadioButton("Otro");

// Establecer posiciones
rbMasculino.setBounds(10, 50, 100, 25);
rbFemenino.setBounds(10, 75, 100, 25);
rbOtro.setBounds(10, 100, 100, 25);

// IMPORTANTE: Crear ButtonGroup para agruparlos
ButtonGroup grupoGenero = new ButtonGroup();
grupoGenero.add(rbMasculino);
grupoGenero.add(rbFemenino);
grupoGenero.add(rbOtro);

// Seleccionar uno por defecto
rbMasculino.setSelected(true);

// Agregar al frame
frame.add(rbMasculino);
frame.add(rbFemenino);
frame.add(rbOtro);

// Verificar cuál está seleccionado
if (rbMasculino.isSelected()) {
    System.out.println("Seleccionó Masculino");
}
```

**¿Por qué necesitamos ButtonGroup?**
Sin `ButtonGroup`, todos los radio buttons podrían estar seleccionados al mismo tiempo, lo cual no es el comportamiento deseado. El `ButtonGroup` garantiza que solo uno esté seleccionado.

**Métodos importantes:**

| Método | Descripción |
|--------|-------------|
| `isSelected()` | Devuelve true si está seleccionado |
| `setSelected(boolean)` | Selecciona/deselecciona |
| `getText()` | Obtiene el texto del botón |

### 3.5 JCheckBox - Casillas de Verificación

Las casillas de verificación (`JCheckBox`) permiten seleccionar MÚLTIPLES opciones.

**Sintaxis básica:**
```java
JCheckBox checkbox = new JCheckBox("Texto");
```

**Ejemplo completo:**
```java
// Crear checkboxes
JCheckBox cbxJava = new JCheckBox("Java");
JCheckBox cbxPython = new JCheckBox("Python");
JCheckBox cbxCpp = new JCheckBox("C++");

// Establecer posiciones
cbxJava.setBounds(10, 50, 100, 25);
cbxPython.setBounds(10, 75, 100, 25);
cbxCpp.setBounds(10, 100, 100, 25);

// Seleccionar uno por defecto
cbxJava.setSelected(true);

// Agregar al frame
frame.add(cbxJava);
frame.add(cbxPython);
frame.add(cbxCpp);

// Verificar cuáles están seleccionados
if (cbxJava.isSelected()) {
    System.out.println("Java seleccionado");
}
if (cbxPython.isSelected()) {
    System.out.println("Python seleccionado");
}
```

**Diferencia entre JRadioButton y JCheckBox:**
- **JRadioButton:** Solo UNO puede estar seleccionado (excluyente)
- **JCheckBox:** VARIOS pueden estar seleccionados (no excluyente)

---

## 4. Manejo de Eventos

### 4.1 ¿Qué son los Eventos?

Los **eventos** son acciones que realiza el usuario sobre la interfaz gráfica, como:
- Hacer clic en un botón
- Presionar una tecla
- Mover el mouse
- Cerrar una ventana
- Escribir en un campo de texto

### 4.2 ¿Qué son los Listeners?

Los **Listeners** (escuchadores u oyentes) son objetos que "escuchan" y responden a los eventos. Cuando ocurre un evento, el listener ejecuta código específico.

**Analogía:** Imagina que el Listener es como un guardia de seguridad que está atento a cuando alguien toca la puerta (evento). Cuando detecta que alguien tocó, ejecuta una acción (abrir la puerta, pedir identificación, etc.)

### 4.3 ActionListener - El Listener Más Usado

`ActionListener` es una interfaz que se usa para detectar "acciones" del usuario, principalmente:
- Clic en un botón
- Presionar Enter en un campo de texto
- Seleccionar un ítem de menú

**Estructura básica:**

```java
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;

public class MiClase implements ActionListener {
    
    @Override
    public void actionPerformed(ActionEvent e) {
        // Código que se ejecuta cuando ocurre el evento
        System.out.println("¡Evento detectado!");
    }
}
```

**Pasos para usar ActionListener:**

1. **Implementar la interfaz ActionListener**
2. **Sobrescribir el método actionPerformed()**
3. **Registrar el listener en el componente**

### 4.4 Tres Formas de Implementar ActionListener

#### **Forma 1: La clase principal implementa ActionListener**

```java
import javax.swing.*;
import java.awt.event.*;

public class VentanaConBoton extends JFrame implements ActionListener {
    
    private JButton btnSaludar;
    private JLabel lblMensaje;
    
    public VentanaConBoton() {
        setTitle("Ejemplo de Evento");
        setSize(300, 150);
        setLayout(null);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        
        // Crear componentes
        btnSaludar = new JButton("Saludar");
        btnSaludar.setBounds(50, 20, 100, 30);
        
        lblMensaje = new JLabel("");
        lblMensaje.setBounds(50, 60, 200, 30);
        
        // IMPORTANTE: Registrar el listener
        btnSaludar.addActionListener(this);
        // "this" significa "esta misma clase"
        
        // Agregar a la ventana
        add(btnSaludar);
        add(lblMensaje);
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        // Este método se ejecuta cuando se hace clic en el botón
        lblMensaje.setText("¡Hola Mundo!");
    }
    
    public static void main(String[] args) {
        VentanaConBoton ventana = new VentanaConBoton();
        ventana.setVisible(true);
    }
}
```

**Explicación línea por línea:**

1. `implements ActionListener` - Indica que esta clase va a manejar eventos
2. `btnSaludar.addActionListener(this)` - Registra el botón para que "escuche" eventos. El `this` significa "usa el método actionPerformed de ESTA clase"
3. `actionPerformed(ActionEvent e)` - Método que se ejecuta automáticamente cuando hay un clic

#### **Forma 2: Clase Anónima (Más limpia para eventos simples)**

```java
import javax.swing.*;
import java.awt.event.*;

public class VentanaConBoton2 extends JFrame {
    
    public VentanaConBoton2() {
        setTitle("Ejemplo con Clase Anónima");
        setSize(300, 150);
        setLayout(null);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        
        JButton btnSaludar = new JButton("Saludar");
        btnSaludar.setBounds(50, 20, 100, 30);
        
        JLabel lblMensaje = new JLabel("");
        lblMensaje.setBounds(50, 60, 200, 30);
        
        // CLASE ANÓNIMA - se crea y usa en el mismo lugar
        btnSaludar.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                lblMensaje.setText("¡Hola desde clase anónima!");
            }
        });
        
        add(btnSaludar);
        add(lblMensaje);
    }
    
    public static void main(String[] args) {
        new VentanaConBoton2().setVisible(true);
    }
}
```

**Ventajas de la clase anónima:**
- El código del evento está junto al componente
- Más fácil de leer para eventos simples
- No necesita implementar ActionListener en la clase principal

#### **Forma 3: Lambda Expression (Java 8+) - LA MÁS MODERNA**

```java
btnSaludar.addActionListener(e -> {
    lblMensaje.setText("¡Hola desde lambda!");
});

// Si es una sola línea, se puede simplificar:
btnSaludar.addActionListener(e -> lblMensaje.setText("¡Hola!"));
```

**Ventajas de lambda:**
- Código más corto y limpio
- Sintaxis moderna de Java
- Fácil de leer

### 4.5 Detectar Qué Botón Fue Presionado

Cuando tenemos múltiples botones con el mismo ActionListener, necesitamos saber cuál fue presionado.

**Método 1: Usar getSource()**

```java
public void actionPerformed(ActionEvent e) {
    Object fuente = e.getSource();
    
    if (fuente == btnSuma) {
        // El botón de suma fue presionado
        resultado = num1 + num2;
    } else if (fuente == btnResta) {
        // El botón de resta fue presionado
        resultado = num1 - num2;
    }
}
```

**Método 2: Usar getActionCommand() con setActionCommand()**

```java
// Configurar comandos
btnSuma.setActionCommand("SUMAR");
btnResta.setActionCommand("RESTAR");

// En actionPerformed:
public void actionPerformed(ActionEvent e) {
    String comando = e.getActionCommand();
    
    if (comando.equals("SUMAR")) {
        resultado = num1 + num2;
    } else if (comando.equals("RESTAR")) {
        resultado = num1 - num2;
    }
}
```

### 4.6 Conversión de Tipos de Datos

En las aplicaciones GUI, frecuentemente necesitamos convertir entre String y números:

**De String a Int:**
```java
String texto = txtNumero.getText();
int numero = Integer.parseInt(texto);
```

**De String a Double:**
```java
String texto = txtNumero.getText();
double numero = Double.parseDouble(texto);
```

**De String a Float:**
```java
String texto = txtNumero.getText();
float numero = Float.parseFloat(texto);
```

**De número a String:**
```java
int numero = 42;
String texto = String.valueOf(numero);
// o simplemente:
String texto = "" + numero;
```

**IMPORTANTE: Manejo de Errores**

Si el usuario ingresa texto no numérico, `parseInt()` o `parseDouble()` lanzarán una excepción. Usa try-catch:

```java
try {
    String texto = txtNumero.getText();
    int numero = Integer.parseInt(texto);
    // Usar el número...
} catch (NumberFormatException ex) {
    JOptionPane.showMessageDialog(this, 
        "Por favor ingrese un número válido", 
        "Error", 
        JOptionPane.ERROR_MESSAGE);
}
```

---

## 5. Layout Managers

Los **Layout Managers** (administradores de diseño) controlan cómo se posicionan y dimensionan los componentes dentro de un contenedor.

### 5.1 Null Layout (Diseño Absoluto)

Con `setLayout(null)`, posicionamos los componentes manualmente usando `setBounds()`.

```java
setLayout(null); // Desactiva el layout manager

JButton boton = new JButton("Click");
boton.setBounds(10, 10, 100, 30);
// setBounds(x, y, width, height)
```

**Ventajas:**
- Control total sobre la posición
- Útil para diseños complejos

**Desventajas:**
- No se adapta a diferentes tamaños de ventana
- Más trabajo manual

### 5.2 FlowLayout

Coloca componentes de izquierda a derecha, como texto en un párrafo.

```java
setLayout(new FlowLayout());

add(new JButton("Botón 1"));
add(new JButton("Botón 2"));
add(new JButton("Botón 3"));
```

### 5.3 BorderLayout

Divide el contenedor en 5 regiones: NORTH, SOUTH, EAST, WEST, CENTER.

```java
setLayout(new BorderLayout());

add(new JButton("Norte"), BorderLayout.NORTH);
add(new JButton("Sur"), BorderLayout.SOUTH);
add(new JButton("Este"), BorderLayout.EAST);
add(new JButton("Oeste"), BorderLayout.WEST);
add(new JButton("Centro"), BorderLayout.CENTER);
```

### 5.4 GridLayout

Organiza componentes en una cuadrícula de filas y columnas.

```java
setLayout(new GridLayout(3, 2)); // 3 filas, 2 columnas

add(new JButton("1"));
add(new JButton("2"));
add(new JButton("3"));
add(new JButton("4"));
add(new JButton("5"));
add(new JButton("6"));
```

**En este curso usaremos principalmente Null Layout con setBounds().**

---

# PARTE II: ANÁLISIS DETALLADO DE PROYECTOS

En esta sección analizaremos cada uno de los 15 proyectos, explicando:
- Objetivo del programa
- Componentes utilizados
- Análisis del código línea por línea
- Conceptos clave aplicados
- Diagramas de flujo
- Capturas de pantalla conceptuales

Los proyectos están organizados por nivel de dificultad: básico, intermedio y avanzado.

---

## NIVEL BÁSICO - PRIMEROS PASOS

### 6. EjemploGUI_1

**📁 Ubicación:** `/Ejercicios-Ejemplos/EjemploGUI_1/src/ejemplogui_1/EjemploGUI_1.java`

#### Objetivo del Programa
Crear la ventana más básica posible con Java Swing. Este es el "Hola Mundo" de las interfaces gráficas.

#### Componentes Utilizados
- JFrame (ventana)

#### Código Completo con Análisis

```java
package ejemplogui_1;

import javax.swing.JFrame;

public class EjemploGUI_1 extends JFrame {
    
    public EjemploGUI_1() {
        this.setSize(400,300);
    }

    public static void main(String[] args) {
        EjemploGUI_1 GUI = new EjemploGUI_1();
        GUI.setVisible(true);
    }
}
```

#### Análisis Línea por Línea

**Línea 1:** `package ejemplogui_1;`
- Declaración del paquete (carpeta) donde está la clase
- Los paquetes organizan las clases en Java
- El nombre debe coincidir con la estructura de carpetas

**Línea 3:** `import javax.swing.JFrame;`
- Importa la clase JFrame del paquete javax.swing
- JFrame es la clase que representa una ventana
- Sin este import, no podríamos usar JFrame

**Línea 5:** `public class EjemploGUI_1 extends JFrame {`
- `public`: La clase es accesible desde cualquier parte
- `class EjemploGUI_1`: Nombre de nuestra clase
- `extends JFrame`: **HERENCIA** - nuestra clase ES UN JFrame
  - Hereda todos los métodos de JFrame (setSize, setVisible, etc.)
  - Es como decir "EjemploGUI_1 es un tipo especial de ventana"

**Línea 7-9:** Constructor de la clase
```java
public EjemploGUI_1() {
    this.setSize(400,300);
}
```
- `public EjemploGUI_1()`: Constructor (se ejecuta al crear el objeto)
- `this.setSize(400,300)`: 
  - `this` se refiere al objeto actual (la ventana)
  - `setSize()` es un método heredado de JFrame
  - `400` = ancho en píxeles
  - `300` = alto en píxeles

**Línea 11-14:** Método main (punto de entrada del programa)
```java
public static void main(String[] args) {
    EjemploGUI_1 GUI = new EjemploGUI_1();
    GUI.setVisible(true);
}
```
- `public static void main`: Método principal que ejecuta Java
- `EjemploGUI_1 GUI = new EjemploGUI_1()`:
  - Crea un objeto de tipo EjemploGUI_1
  - Al crearlo, se ejecuta el constructor (línea 7-9)
  - `GUI` es el nombre de la variable que guarda la ventana
- `GUI.setVisible(true)`:
  - Hace visible la ventana
  - Por defecto las ventanas están ocultas
  - `true` = mostrar, `false` = ocultar

#### Conceptos Clave

1. **Herencia:** `extends JFrame` permite que nuestra clase tenga todas las capacidades de una ventana
2. **Constructor:** Se ejecuta automáticamente al crear un objeto
3. **this:** Referencia al objeto actual
4. **Método main:** Punto de entrada del programa

#### Diagrama de Flujo

```
┌─────────────────────────┐
│  Programa Inicia        │
│  (método main)          │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│  Crear objeto           │
│  GUI = new EjemploGUI_1 │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│  Constructor se ejecuta │
│  setSize(400, 300)      │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│  Hacer visible ventana  │
│  setVisible(true)       │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│  Ventana mostrada       │
│  Programa corriendo     │
└─────────────────────────┘
```

#### Problemas de Este Código

1. **No tiene setDefaultCloseOperation():** Al cerrar la ventana, el programa sigue corriendo en segundo plano
2. **Ventana vacía:** No tiene componentes (botones, etiquetas, etc.)
3. **Sin título:** La ventana no tiene título

#### Versión Mejorada

```java
package ejemplogui_1;

import javax.swing.JFrame;

public class EjemploGUI_1_Mejorado extends JFrame {
    
    public EjemploGUI_1_Mejorado() {
        // Título de la ventana
        setTitle("Mi Primera Ventana");
        
        // Tamaño
        setSize(400, 300);
        
        // Centrar en la pantalla
        setLocationRelativeTo(null);
        
        // Cerrar el programa al cerrar la ventana
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        EjemploGUI_1_Mejorado GUI = new EjemploGUI_1_Mejorado();
        GUI.setVisible(true);
    }
}
```

#### Ejercicio Propuesto

Modifica el programa para que:
1. Tenga un tamaño de 600x400 píxeles
2. Tenga el título "Ventana de Práctica"
3. No permita redimensionar la ventana (investiga qué método usar)

---

### 7. ejemplogui

**📁 Ubicación:** `/Ejercicios-Ejemplos/ejemplogui/src/ejemplogui/Ejemplogui.java`

#### Objetivo del Programa
Similar al anterior, pero con configuración más completa de la ventana.

#### Código Completo

```java
package ejemplogui;

import javax.swing.JFrame;

public class Ejemplogui extends JFrame {
    
    public static void main(String[] args) {
        Ejemplogui GUI = new Ejemplogui();
        GUI.setVisible(true);
        GUI.setBounds(300,200,340,330);
        GUI.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}
```

#### Análisis Línea por Línea

**Línea 11:** `GUI.setBounds(300,200,340,330);`
- `setBounds(x, y, width, height)` establece:
  - Posición X: 300 píxeles desde el borde izquierdo de la pantalla
  - Posición Y: 200 píxeles desde el borde superior de la pantalla
  - Ancho: 340 píxeles
  - Alto: 330 píxeles

**Diferencia con EjemploGUI_1:**
- Usa `setBounds()` en lugar de `setSize()`
- `setBounds()` controla posición Y tamaño al mismo tiempo
- Incluye `setDefaultCloseOperation()` (¡importante!)

**Línea 12:** `setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);`
- **EXIT_ON_CLOSE (3):** Termina completamente la aplicación
- Sin esta línea, al cerrar la ventana el programa sigue corriendo
- **MUY IMPORTANTE:** Siempre incluir esta línea

#### Comparación setBounds() vs setSize() + setLocation()

```java
// Opción 1: setBounds (todo en uno)
frame.setBounds(100, 50, 400, 300);

// Opción 2: setSize + setLocation (separado)
frame.setSize(400, 300);      // Tamaño
frame.setLocation(100, 50);   // Posición

// Opción 3: setSize + centrar
frame.setSize(400, 300);
frame.setLocationRelativeTo(null); // Centra en pantalla
```

#### Concepto: Sistema de Coordenadas

```
(0,0) ─────────────► X (ancho)
  │
  │    ┌──────────────┐
  │    │   Ventana    │ Posición (300, 200)
  │    │              │ Tamaño 340x330
  │    │              │
  │    └──────────────┘
  │
  ▼ Y (alto)
```

- Origen (0,0) está en la esquina superior izquierda de la pantalla
- X aumenta hacia la derecha
- Y aumenta hacia abajo

---

### 8. Test

**📁 Ubicación:** `/Ejercicios-Ejemplos/Test/src/main/java/com/mycompany/test/Test.java`

#### Objetivo del Programa
Proyecto plantilla básica creada con Maven o IDE.

#### Código

```java
package com.mycompany.test;

public class Test {

    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

#### Análisis

Este es un proyecto básico que:
- No tiene interfaz gráfica
- Solo imprime "Hello World!" en consola
- Sirve como plantilla para crear proyectos

**Nota:** Este proyecto no tiene componentes Swing, es solo un proyecto de consola estándar.

---

## NIVEL INTERMEDIO - COMPONENTES INTERACTIVOS

### 9. Bienvenida

**📁 Ubicación:** `/Ejercicios-Ejemplos/Bienvenida/src/bienvenida/`

#### Objetivo del Programa
Crear un formulario interactivo con varios componentes: etiquetas, campos de texto, botones y radio buttons.

#### Archivos del Proyecto

1. **Bienvenida.java** - Clase principal (main)
2. **Formulario.java** - La ventana con todos los componentes
3. **Formulario.form** - Archivo de diseño visual (NetBeans)

#### Código de Bienvenida.java

```java
package bienvenida;

public class Bienvenida {
    
    public static void main(String[] args) {
        Formulario GUI=new Formulario();
        GUI.setVisible(true);
    }
}
```

**Análisis:**
- Clase simple que solo crea y muestra la ventana Formulario
- Patrón de separación: una clase para main, otra para la interfaz
- `Formulario GUI = new Formulario()` crea la ventana
- `GUI.setVisible(true)` la muestra

#### Código de Formulario.java (Parcial - Versión Simplificada)

```java
package bienvenida;

import javax.swing.*;
import java.awt.event.*;

public class Formulario extends javax.swing.JFrame {
    
    // Declaración de componentes
    private javax.swing.ButtonGroup grupo1;
    private javax.swing.JLabel jLabel1;
    private javax.swing.JLabel jLabel2;
    private javax.swing.JTextField caja1;
    private javax.swing.JTextField caja2;
    private javax.swing.JButton Boton1;
    private javax.swing.JButton Boton2;
    private javax.swing.JRadioButton rad1;
    private javax.swing.JRadioButton rad2;

    public Formulario() {
        initComponents();
    }

    private void initComponents() {
        // Crear el ButtonGroup
        grupo1 = new javax.swing.ButtonGroup();
        
        // Crear etiquetas
        jLabel1 = new javax.swing.JLabel();
        jLabel2 = new javax.swing.JLabel();
        
        // Crear campos de texto
        caja1 = new javax.swing.JTextField();
        caja2 = new javax.swing.JTextField();
        
        // Crear botones
        Boton1 = new javax.swing.JButton();
        Boton2 = new javax.swing.JButton();
        
        // Crear radio buttons
        rad1 = new javax.swing.JRadioButton();
        rad2 = new javax.swing.JRadioButton();
        
        // Configurar la ventana
        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);
        
        // Configurar etiqueta 1
        jLabel1.setFont(new java.awt.Font("Arial", 0, 24));
        jLabel1.setForeground(new java.awt.Color(0, 0, 225));
        jLabel1.setText("Primer programa con GUI");
        
        // Configurar etiqueta 2
        jLabel2.setFont(new java.awt.Font("Arial", 0, 14));
        jLabel2.setForeground(new java.awt.Color(255, 0, 0));
        jLabel2.setText("Escribe tu nombre:");
        
        // Configurar campo de texto 1
        caja1.setFont(new java.awt.Font("Arial", 0, 14));
        caja1.setForeground(new java.awt.Color(225, 0, 0));
        
        // Configurar botones
        Boton1.setFont(new java.awt.Font("Arial", 0, 14));
        Boton1.setText("Aceptar");
        Boton1.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                Boton1ActionPerformed(evt);
            }
        });
        
        Boton2.setFont(new java.awt.Font("Arial", 0, 14));
        Boton2.setText("Borrar");
        
        // Configurar radio buttons
        grupo1.add(rad1);
        rad1.setText("Hombre");
        
        grupo1.add(rad2);
        rad2.setText("Mujer");
        
        // Layout automático (generado por NetBeans)
        // ... código de posicionamiento ...
        
        pack();
    }
    
    private void Boton1ActionPerformed(java.awt.event.ActionEvent evt) {
        // Código que se ejecuta al presionar el botón "Aceptar"
        String nombre = caja1.getText();
        JOptionPane.showMessageDialog(this, "Bienvenido/a " + nombre);
    }
}
```

#### Análisis Detallado de Conceptos

**1. Declaración de Variables de Instancia**

```java
private javax.swing.JLabel jLabel1;
private javax.swing.JTextField caja1;
```

- `private`: Solo esta clase puede acceder a estas variables
- Son variables de **instancia** (pertenecen al objeto, no son locales)
- Se declaran fuera de los métodos para que todos los métodos puedan usarlas

**2. ButtonGroup - Agrupación de Radio Buttons**

```java
grupo1 = new javax.swing.ButtonGroup();
grupo1.add(rad1);
grupo1.add(rad2);
```

- `ButtonGroup` garantiza que solo UN radio button esté seleccionado
- NO es un componente visual, es lógico
- Cada radio button se agrega al grupo con `add()`

**3. Configuración de Fuentes**

```java
jLabel1.setFont(new java.awt.Font("Arial", 0, 24));
```

- `Font(nombre, estilo, tamaño)`
- Nombre: "Arial", "Times New Roman", "Courier", etc.
- Estilo:
  - `0` o `Font.PLAIN` = Normal
  - `1` o `Font.BOLD` = Negrita
  - `2` o `Font.ITALIC` = Cursiva
  - `3` o `Font.BOLD | Font.ITALIC` = Negrita y cursiva
- Tamaño: en puntos

**4. Configuración de Colores**

```java
jLabel1.setForeground(new java.awt.Color(0, 0, 225));
```

- `Color(rojo, verde, azul)` - valores de 0 a 255
- `Color(0, 0, 225)` = azul
- `Color(255, 0, 0)` = rojo
- `Color(0, 255, 0)` = verde
- `Color(255, 255, 255)` = blanco
- `Color(0, 0, 0)` = negro

También se pueden usar constantes predefinidas:
```java
setForeground(Color.RED);
setForeground(Color.BLUE);
setForeground(Color.GREEN);
```

**5. Evento del Botón - Clase Anónima**

```java
Boton1.addActionListener(new java.awt.event.ActionListener() {
    public void actionPerformed(java.awt.event.ActionEvent evt) {
        Boton1ActionPerformed(evt);
    }
});
```

- Se crea una clase anónima que implementa ActionListener
- Cuando se hace clic, llama al método `Boton1ActionPerformed`

**6. Obtener Texto de un JTextField**

```java
String nombre = caja1.getText();
```

- `getText()` devuelve el texto como String
- Si el campo está vacío, devuelve `""`

**7. Mostrar Mensaje con JOptionPane**

```java
JOptionPane.showMessageDialog(this, "Bienvenido/a " + nombre);
```

- Muestra una ventana emergente con un mensaje
- `this` es la ventana padre
- El mensaje puede concatenar texto y variables

#### Diagrama de Componentes

```
┌────────────────────────────────────────────┐
│   Formulario (JFrame)                      │
│                                            │
│  ┌──────────────────────────────────────┐ │
│  │ "Primer programa con GUI" (JLabel1)  │ │
│  └──────────────────────────────────────┘ │
│                                            │
│  ┌──────────────────────────┐             │
│  │ "Escribe tu nombre:" (JLabel2)         │
│  └──────────────────────────┘             │
│                                            │
│  ┌──────────────────────────────────────┐ │
│  │ [          ] (caja1 - JTextField)    │ │
│  └──────────────────────────────────────┘ │
│                                            │
│  ○ Hombre (rad1)                          │
│  ○ Mujer (rad2)                           │
│  └─ grupo1 (ButtonGroup)                  │
│                                            │
│  ┌──────────┐  ┌──────────┐              │
│  │ Aceptar  │  │  Borrar  │              │
│  │ (Boton1) │  │ (Boton2) │              │
│  └──────────┘  └──────────┘              │
│                                            │
│  ┌──────────────────────────────────────┐ │
│  │ [          ] (caja2 - JTextField)    │ │
│  └──────────────────────────────────────┘ │
└────────────────────────────────────────────┘
```

#### Flujo del Programa

```
Usuario abre la aplicación
         │
         ▼
┌─────────────────────────┐
│  Formulario se crea     │
│  initComponents()       │
│  - Crea componentes     │
│  - Configura propiedades│
│  - Establece layout     │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ Usuario escribe nombre  │
│ en caja1                │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ Usuario selecciona      │
│ radio button            │
│ (Hombre o Mujer)        │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ Usuario hace clic en    │
│ botón "Aceptar"         │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ actionPerformed ejecuta │
│ - Obtiene texto (getText)│
│ - Muestra mensaje       │
└─────────────────────────┘
```

#### Conceptos Avanzados

**1. ¿Por qué usar initComponents()?**

Separar la inicialización en un método tiene ventajas:
- Código más organizado
- Fácil de mantener
- Los IDEs como NetBeans lo generan automáticamente
- Permite regenerar el código sin perder la lógica

**2. Variables de Instancia vs Variables Locales**

```java
public class Ejemplo {
    private JButton boton; // Variable de instancia
    
    public void metodo1() {
        int x = 5; // Variable local
        boton.setText("OK"); // ✓ Acceso a variable de instancia
    }
    
    public void metodo2() {
        boton.setText("Cancel"); // ✓ Acceso a variable de instancia
        // System.out.println(x); // ✗ ERROR - x no existe aquí
    }
}
```

#### Ejercicio Propuesto

Modifica el programa Bienvenida para que:
1. Agregue un tercer radio button "Otro"
2. El botón "Borrar" limpie todos los campos de texto
3. Al presionar "Aceptar", muestre también qué opción de género se seleccionó

**Código del botón Borrar:**
```java
Boton2.addActionListener(e -> {
    caja1.setText("");
    caja2.setText("");
});
```

**Código mejorado del botón Aceptar:**
```java
private void Boton1ActionPerformed(ActionEvent evt) {
    String nombre = caja1.getText();
    String genero = "";
    
    if (rad1.isSelected()) {
        genero = "Hombre";
    } else if (rad2.isSelected()) {
        genero = "Mujer";
    }
    
    JOptionPane.showMessageDialog(this, 
        "Bienvenido/a " + nombre + "\nGénero: " + genero);
}
```

---

### 10. CambiarTitulo

**📁 Ubicación:** `/Ejercicios-Ejemplos/CambiarTitulo/src/cambiartitulo/CambiarTitulo.java`

#### Objetivo del Programa
Demostrar cómo cambiar dinámicamente el título de una ventana usando un botón.

#### Código Completo

```java
package cambiartitulo;

import javax.swing.JFrame;
import javax.swing.JButton;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;

public class CambiarTitulo extends JFrame implements ActionListener {
    
    private JButton boton;
    
    public CambiarTitulo() {
        // Configurar ventana
        setTitle("Curso de JavaScript");
        setSize(300, 200);
        setLayout(null);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        // Crear botón
        boton = new JButton("Cambiar Título");
        boton.setBounds(70, 70, 150, 30);
        boton.addActionListener(this);
        
        // Agregar botón a la ventana
        add(boton);
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        // Cambiar el título de la ventana
        setTitle("Curso de Java");
    }
    
    public static void main(String[] args) {
        CambiarTitulo ventana = new CambiarTitulo();
        ventana.setVisible(true);
    }
}
```

#### Análisis Línea por Línea

**Línea 8:** `public class CambiarTitulo extends JFrame implements ActionListener {`
- `extends JFrame`: Hereda de JFrame (es una ventana)
- `implements ActionListener`: Implementa la interfaz para manejar eventos
- Puede hacer AMBAS cosas: heredar de una clase E implementar interfaces

**Línea 10:** `private JButton boton;`
- Variable de instancia (pertenece al objeto)
- `private`: solo esta clase puede acceder
- Se declara fuera del constructor para que todos los métodos la vean

**Línea 13:** `setTitle("Curso de JavaScript");`
- Establece el título inicial de la ventana
- Se puede cambiar en cualquier momento

**Línea 14:** `setSize(300, 200);`
- Ancho: 300 píxeles
- Alto: 200 píxeles

**Línea 15:** `setLayout(null);`
- Desactiva el layout manager
- Permite usar setBounds() para posicionar componentes manualmente

**Línea 19-20:**
```java
boton = new JButton("Cambiar Título");
boton.setBounds(70, 70, 150, 30);
```
- Crea el botón con el texto "Cambiar Título"
- `setBounds(x, y, ancho, alto)`:
  - x: 70 px desde la izquierda
  - y: 70 px desde arriba
  - ancho: 150 px
  - alto: 30 px

**Línea 21:** `boton.addActionListener(this);`
- **MUY IMPORTANTE**: Registra el botón para escuchar eventos
- `this` se refiere a la clase actual (CambiarTitulo)
- Como la clase implementa ActionListener, puede manejar eventos

**Línea 24:** `add(boton);`
- Agrega el botón a la ventana
- Sin esto, el botón no se vería

**Líneas 28-31:** El método actionPerformed
```java
@Override
public void actionPerformed(ActionEvent e) {
    setTitle("Curso de Java");
}
```
- `@Override`: Indica que estamos sobrescribiendo un método de la interfaz
- Se ejecuta automáticamente cuando se hace clic en el botón
- `setTitle()` cambia el título de la ventana

#### Concepto: implements vs extends

```java
// extends = HERENCIA (solo una clase)
class MiVentana extends JFrame {
    // MiVentana ES UNA ventana
}

// implements = IMPLEMENTACIÓN (múltiples interfaces)
class MiVentana implements ActionListener, MouseListener {
    // MiVentana PUEDE manejar eventos
}

// SE PUEDEN COMBINAR
class MiVentana extends JFrame implements ActionListener {
    // MiVentana ES UNA ventana Y PUEDE manejar eventos
}
```

#### Diagrama de Secuencia

```
Usuario           Botón          actionPerformed()    JFrame
  │                │                    │               │
  │   Clic         │                    │               │
  │───────────────>│                    │               │
  │                │  Evento generado   │               │
  │                │───────────────────>│               │
  │                │                    │ setTitle()    │
  │                │                    │──────────────>│
  │                │                    │               │
  │                │                    │  Título       │
  │                │                    │  actualizado  │
  │                │                    │<──────────────│
  │                │                    │               │
```

#### Estados de la Ventana

```
Estado Inicial:
┌─────────────────────────────┐
│ Curso de JavaScript       [_][□][X]
├─────────────────────────────┤
│                             │
│      ┌──────────────┐       │
│      │Cambiar Título│       │
│      └──────────────┘       │
│                             │
└─────────────────────────────┘

       ↓ (Usuario hace clic)

Estado Final:
┌─────────────────────────────┐
│ Curso de Java             [_][□][X]
├─────────────────────────────┤
│                             │
│      ┌──────────────┐       │
│      │Cambiar Título│       │
│      └──────────────┘       │
│                             │
└─────────────────────────────┘
```

#### Variaciones del Programa

**Versión con Lambda (Java 8+):**

```java
public class CambiarTitulo extends JFrame {
    
    public CambiarTitulo() {
        setTitle("Curso de JavaScript");
        setSize(300, 200);
        setLayout(null);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        JButton boton = new JButton("Cambiar Título");
        boton.setBounds(70, 70, 150, 30);
        
        // Lambda en lugar de implements ActionListener
        boton.addActionListener(e -> setTitle("Curso de Java"));
        
        add(boton);
    }
    
    public static void main(String[] args) {
        new CambiarTitulo().setVisible(true);
    }
}
```

**Versión con Contador:**

```java
public class CambiarTituloContador extends JFrame {
    private int contador = 0;
    
    public CambiarTituloContador() {
        setTitle("Contador: 0");
        setSize(300, 200);
        setLayout(null);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        JButton boton = new JButton("Incrementar");
        boton.setBounds(70, 70, 150, 30);
        
        boton.addActionListener(e -> {
            contador++;
            setTitle("Contador: " + contador);
        });
        
        add(boton);
    }
    
    public static void main(String[] args) {
        new CambiarTituloContador().setVisible(true);
    }
}
```

#### Ejercicio Propuesto

Crea un programa con DOS botones:
1. "Modo Día": Cambia el título a "Modo Día Activado" y el fondo a blanco
2. "Modo Noche": Cambia el título a "Modo Noche Activado" y el fondo a negro

**Pistas:**
```java
// Cambiar color de fondo
getContentPane().setBackground(Color.WHITE);
getContentPane().setBackground(Color.BLACK);
```

---

Continúa con más proyectos...


### 11. CajasChequeo

**📁 Ubicación:** `/Ejercicios-Ejemplos/CajasChequeo/src/cajaschequeo/CajasChequeo.java`

#### Objetivo del Programa
Demostrar el uso de casillas de verificación (JCheckBox) para seleccionar múltiples opciones.

#### ⚠️ ADVERTENCIA: Este código tiene un error conceptual
El programa usa `ButtonGroup` con `JCheckBox`, lo cual es **INCORRECTO**. `ButtonGroup` solo debe usarse con `JRadioButton`.

#### Código Completo con Análisis

```java
package cajaschequeo;
import javax.swing.*;
import java.awt.*;

public class CajasChequeo extends JFrame {
    public CajasChequeo() {
        super("Cajas Chequeo");
        setSize(340, 120);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        // Crear checkboxes
        JCheckBox cursoJava = new JCheckBox("Curso de Java", true);
        JCheckBox cursoFlash = new JCheckBox("Curso de flash", false);
        JCheckBox cursoPHP = new JCheckBox("Curso de PHP", false);
        JCheckBox cursoC = new JCheckBox("Curso de C++", false);
        
        // Crear layout
        FlowLayout dis = new FlowLayout();
        
        // ❌ ERROR: ButtonGroup NO se usa con JCheckBox
        ButtonGroup cursos = new ButtonGroup();
        cursos.add(cursoJava);
        cursos.add(cursoFlash);
        cursos.add(cursoPHP);
        cursos.add(cursoC);
        
        setLayout(dis);
        add(cursoJava);
        add(cursoFlash);
        add(cursoPHP);
        add(cursoC);
        setVisible(true);
    }
    
    public static void main(String[] args) {
        CajasChequeo app = new CajasChequeo();
    }
}
```

#### Análisis Línea por Línea

**Línea 7:** `super("Cajas Chequeo");`
- `super()` llama al constructor de la clase padre (JFrame)
- Establece el título de la ventana
- Equivalente a `setTitle("Cajas Chequeo")`

**Línea 11:** `JCheckBox cursoJava = new JCheckBox("Curso de Java", true);`
- Crea un checkbox con el texto "Curso de Java"
- `true` significa que está **seleccionado** por defecto
- `false` significa **no seleccionado**

**Línea 14:** `FlowLayout dis = new FlowLayout();`
- Crea un layout que acomoda componentes de izquierda a derecha
- Como texto en un párrafo
- Cuando se llena una línea, pasa a la siguiente

**Líneas 16-20: ❌ ERROR CONCEPTUAL**
```java
ButtonGroup cursos = new ButtonGroup();
cursos.add(cursoJava);
// ...
```

**¿Cuál es el problema?**
- `ButtonGroup` está diseñado para `JRadioButton`, NO para `JCheckBox`
- Al usarlo con checkboxes, convierte los checkboxes en radio buttons (solo uno seleccionable)
- Esto contradice el propósito de los checkboxes (selección múltiple)

#### Concepto: JCheckBox vs JRadioButton

| Característica | JCheckBox | JRadioButton |
|----------------|-----------|--------------|
| **Selección** | Múltiple | Una sola opción |
| **ButtonGroup** | NO se usa | SÍ se usa |
| **Ejemplo de uso** | Intereses, hobbies, características | Género, estado civil, prioridad |
| **Estado** | Cada uno independiente | Solo uno activo en el grupo |

**Ejemplo correcto de JCheckBox:**

```
¿Qué lenguajes conoces? (puedes marcar varios)
☑ Java
☐ Python
☑ C++
☐ JavaScript
```

**Ejemplo correcto de JRadioButton:**

```
¿Cuál es tu lenguaje favorito? (solo uno)
◉ Java
○ Python
○ C++
○ JavaScript
```

#### Versión CORREGIDA del Programa

```java
package cajaschequeo;
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class CajasChequeoCorregido extends JFrame {
    
    private JCheckBox cursoJava, cursoFlash, cursoPHP, cursoC;
    private JButton btnMostrar;
    
    public CajasChequeoCorregido() {
        super("Selecciona tus cursos");
        setSize(340, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new FlowLayout());
        
        // Crear checkboxes (CORRECTO: sin ButtonGroup)
        cursoJava = new JCheckBox("Curso de Java", true);
        cursoFlash = new JCheckBox("Curso de Flash", false);
        cursoPHP = new JCheckBox("Curso de PHP", false);
        cursoC = new JCheckBox("Curso de C++", false);
        
        // Botón para mostrar selección
        btnMostrar = new JButton("Mostrar Selección");
        btnMostrar.addActionListener(e -> mostrarSeleccion());
        
        // Agregar componentes
        add(new JLabel("Selecciona los cursos que te interesan:"));
        add(cursoJava);
        add(cursoFlash);
        add(cursoPHP);
        add(cursoC);
        add(btnMostrar);
        
        setVisible(true);
    }
    
    private void mostrarSeleccion() {
        StringBuilder cursos = new StringBuilder("Cursos seleccionados:\n");
        
        if (cursoJava.isSelected()) cursos.append("- Java\n");
        if (cursoFlash.isSelected()) cursos.append("- Flash\n");
        if (cursoPHP.isSelected()) cursos.append("- PHP\n");
        if (cursoC.isSelected()) cursos.append("- C++\n");
        
        if (!cursoJava.isSelected() && !cursoFlash.isSelected() && 
            !cursoPHP.isSelected() && !cursoC.isSelected()) {
            cursos.append("Ninguno seleccionado");
        }
        
        JOptionPane.showMessageDialog(this, cursos.toString());
    }
    
    public static void main(String[] args) {
        new CajasChequeoCorregido();
    }
}
```

#### Nuevos Conceptos

**1. StringBuilder para concatenar strings**

```java
StringBuilder texto = new StringBuilder("Inicio: ");
texto.append("Más texto\n");
texto.append("Otra línea\n");
String resultado = texto.toString();
```

- Más eficiente que usar `+` en un bucle
- `append()` agrega texto
- `toString()` convierte a String

**2. Verificar estado de múltiples checkboxes**

```java
if (checkbox1.isSelected() && checkbox2.isSelected()) {
    System.out.println("Ambos seleccionados");
}

if (checkbox1.isSelected() || checkbox2.isSelected()) {
    System.out.println("Al menos uno seleccionado");
}

if (!checkbox1.isSelected()) {
    System.out.println("Checkbox1 NO está seleccionado");
}
```

**3. Operador lógico AND (&&) y OR (||)**

```java
// AND (&&) - TODOS deben ser verdaderos
if (a && b && c) {
    // Se ejecuta solo si a, b Y c son true
}

// OR (||) - AL MENOS UNO debe ser verdadero
if (a || b || c) {
    // Se ejecuta si a O b O c es true
}

// NOT (!) - Invierte el valor
if (!a) {
    // Se ejecuta si a es false
}
```

#### Métodos Importantes de JCheckBox

| Método | Descripción | Ejemplo |
|--------|-------------|---------|
| `isSelected()` | Retorna true si está marcado | `if(cbx.isSelected())` |
| `setSelected(boolean)` | Marca o desmarca | `cbx.setSelected(true)` |
| `setText(String)` | Cambia el texto | `cbx.setText("Nuevo")` |
| `getText()` | Obtiene el texto | `String t = cbx.getText()` |
| `setEnabled(boolean)` | Activa/desactiva | `cbx.setEnabled(false)` |

#### Ejercicio Propuesto

Crea un programa de pizzería donde:
1. El usuario seleccione ingredientes con checkboxes (champiñones, pepperoni, aceitunas, cebolla, pimientos)
2. Cada ingrediente tenga un precio
3. Un botón "Calcular Total" sume el precio de los ingredientes seleccionados
4. Muestre el total en una etiqueta o mensaje

**Pistas:**
```java
double total = 0;
if (cbxChampinones.isSelected()) total += 2.50;
if (cbxPepperoni.isSelected()) total += 3.00;
// ...
lblTotal.setText("Total: $" + total);
```

---

### 12. Playback

**📁 Ubicación:** `/Ejercicios-Ejemplos/Playback/src/playback/Playback.java`

#### Objetivo del Programa
Crear una interfaz simple que simula controles de un reproductor de medios usando FlowLayout.

#### Código Completo

```java
package playback;
//ejemplo de programa de interfaz grafica 28/01/26 creando una ventana
//con botones

import javax.swing.*;
import java.awt.*;

public class Playback extends JFrame {
    public Playback () {
        super("Playback");
        setSize(300, 100);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setVisible(true);
        
        FlowLayout dis = new FlowLayout();
        setLayout(dis);
        
        JButton play = new JButton ("Play");
        JButton stop = new JButton ("Stop");
        JButton pausa = new JButton ("Pausa");
        
        add(play);
        add(stop);
        add(pausa);
        
        setVisible(true);
    }
                
    public static void main(String[] args) {
        Playback pb = new Playback(); //objeto del main
    }
}
```

#### Análisis Detallado

**Líneas 2-3:** Comentarios
```java
//ejemplo de programa de interfaz grafica 28/01/26 creando una ventana
//con botones
```
- Comentarios de una línea empiezan con `//`
- Buenos comentarios explican el propósito del código
- Incluyen fecha de creación

**Línea 15-16:** FlowLayout
```java
FlowLayout dis = new FlowLayout();
setLayout(dis);
```
- Crea un layout de flujo
- Los componentes se colocan de izquierda a derecha
- Cuando se llena una fila, pasa a la siguiente

**Línea 13:** `setVisible(true);` ANTES de crear componentes
- ⚠️ Esto es un orden incorrecto
- Los componentes se deberían crear ANTES de hacer visible la ventana
- Aunque funciona, no es buena práctica

**Línea 25:** `setVisible(true);` de nuevo
- Se llama dos veces (línea 13 y 25)
- La segunda es redundante

#### Orden Correcto de Inicialización

```java
public MiVentana() {
    // 1. Configurar propiedades de la ventana
    setTitle("Mi Ventana");
    setSize(400, 300);
    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    setLayout(new FlowLayout());
    
    // 2. Crear componentes
    JButton btn1 = new JButton("Botón 1");
    JButton btn2 = new JButton("Botón 2");
    
    // 3. Agregar componentes
    add(btn1);
    add(btn2);
    
    // 4. Hacer visible (ÚLTIMO PASO)
    setVisible(true);
}
```

#### FlowLayout en Detalle

**¿Cómo funciona FlowLayout?**

Imagina que los componentes son palabras en un párrafo:

```
┌────────────────────────────────────────┐
│ [Play] [Stop] [Pausa]                  │
└────────────────────────────────────────┘
```

Si la ventana es más angosta:

```
┌──────────────────────┐
│ [Play] [Stop]        │
│ [Pausa]              │
└──────────────────────┘
```

**Constructores de FlowLayout:**

```java
// Alineación por defecto (CENTRO)
new FlowLayout();

// Alineación específica
new FlowLayout(FlowLayout.LEFT);    // Izquierda
new FlowLayout(FlowLayout.CENTER);  // Centro
new FlowLayout(FlowLayout.RIGHT);   // Derecha

// Con espaciado personalizado
new FlowLayout(FlowLayout.CENTER, 10, 5);
// 10 = espacio horizontal entre componentes
// 5 = espacio vertical entre filas
```

#### Comparación de Layouts

```
┌─ FlowLayout ──────────┐  ┌─ GridLayout(2,2) ──┐
│ [1] [2] [3]           │  │ [1]    │    [2]    │
│ [4]                   │  │ ────────────────── │
└───────────────────────┘  │ [3]    │    [4]    │
                           └────────────────────┘

┌─ BorderLayout ────────┐  ┌─ Null (setBounds) ─┐
│      [Norte]          │  │  [1]               │
│ [O] [Centro] [E]      │  │         [2]        │
│      [Sur]            │  │    [3]       [4]   │
└───────────────────────┘  └────────────────────┘
```

#### Versión Mejorada con Funcionalidad

```java
package playback;
import javax.swing.*;
import java.awt.*;

public class PlaybackMejorado extends JFrame {
    
    private JLabel lblEstado;
    
    public PlaybackMejorado() {
        super("Reproductor");
        setSize(300, 150);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new FlowLayout());
        
        // Etiqueta de estado
        lblEstado = new JLabel("Estado: Detenido");
        lblEstado.setFont(new Font("Arial", Font.BOLD, 14));
        
        // Botones
        JButton play = new JButton("▶ Play");
        JButton stop = new JButton("⏹ Stop");
        JButton pausa = new JButton("⏸ Pausa");
        
        // Eventos
        play.addActionListener(e -> lblEstado.setText("Estado: Reproduciendo"));
        stop.addActionListener(e -> lblEstado.setText("Estado: Detenido"));
        pausa.addActionListener(e -> lblEstado.setText("Estado: Pausado"));
        
        // Cambiar colores
        play.setBackground(new Color(0, 200, 0));  // Verde
        stop.setBackground(new Color(200, 0, 0));  // Rojo
        pausa.setBackground(new Color(200, 200, 0)); // Amarillo
        
        // Agregar componentes
        add(lblEstado);
        add(play);
        add(stop);
        add(pausa);
        
        setVisible(true);
    }
    
    public static void main(String[] args) {
        new PlaybackMejorado();
    }
}
```

**Nuevos conceptos en la versión mejorada:**

1. **Símbolos Unicode en botones:** `▶ ⏹ ⏸`
2. **Lambdas múltiples:** Un lambda por cada botón
3. **Color personalizado:** `new Color(rojo, verde, azul)`
4. **Variable de instancia compartida:** `lblEstado` usada por todos los eventos

---

### 19. practica5 - Conversor de Unidades

**📁 Ubicación:** `/Ejercicios-Ejemplos/practica5/src/main/java/com/mycompany/practica5/`

#### Objetivo del Programa
Crear un conversor que transforme litros a diferentes unidades de volumen: mililitros, galones, onzas y metros cúbicos. Este es un programa más complejo que integra varios conceptos.

#### Componentes Utilizados
- JFrame (ventana)
- JLabel (etiquetas)
- JTextField (entrada/salida de datos)
- JRadioButton (selección de unidad de conversión)
- ButtonGroup (agrupar radio buttons)
- JButton (botones de acción)
- ActionListener (eventos)

#### Código Simplificado y Comentado

```java
package com.mycompany.practica5;

import javax.swing.*;
import java.awt.event.*;

public class conversiones extends javax.swing.JFrame {
    
    // Componentes de la interfaz
    private javax.swing.ButtonGroup conversiones;
    private javax.swing.JLabel titulo;
    private javax.swing.JLabel jLabel1;
    private javax.swing.JTextField resultado;  // Entrada: litros
    private javax.swing.JButton convertir;
    private javax.swing.JButton Salir;
    private javax.swing.JRadioButton ml;      // Mililitros
    private javax.swing.JRadioButton galon;   // Galones
    private javax.swing.JRadioButton oz;      // Onzas
    private javax.swing.JRadioButton m3;      // Metros cúbicos
    private javax.swing.JLabel resul;         // Salida: resultado
    
    public conversiones() {
        initComponents();
    }
    
    private void initComponents() {
        // Crear ButtonGroup para radio buttons
        conversiones = new javax.swing.ButtonGroup();
        
        // Crear componentes
        titulo = new javax.swing.JLabel();
        jLabel1 = new javax.swing.JLabel();
        resultado = new javax.swing.JTextField();
        convertir = new javax.swing.JButton();
        Salir = new javax.swing.JButton();
        ml = new javax.swing.JRadioButton();
        galon = new javax.swing.JRadioButton();
        oz = new javax.swing.JRadioButton();
        m3 = new javax.swing.JRadioButton();
        resul = new javax.swing.JLabel();
        
        // Configurar ventana
        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);
        setTitle("Conversor de Unidades");
        
        // Configurar etiqueta de título
        titulo.setFont(new java.awt.Font("Inter", 0, 12));
        titulo.setText("CONVERSIONES");
        
        // Configurar etiqueta "Litros:"
        jLabel1.setText("Litros:");
        
        // Configurar botón Convertir
        convertir.setBackground(new java.awt.Color(0, 102, 0));
        convertir.setText("Convertir ->");
        convertir.addActionListener(this::convertirActionPerformed);
        
        // Configurar botón Salir
        Salir.setBackground(new java.awt.Color(204, 0, 0));
        Salir.setText("Salir");
        Salir.addActionListener(this::SalirActionPerformed);
        
        // Configurar radio buttons
        conversiones.add(ml);
        ml.setText("Mililitros");
        
        conversiones.add(galon);
        galon.setText("Galón");
        
        conversiones.add(oz);
        oz.setText("Onza");
        
        conversiones.add(m3);
        m3.setText("M³");
        
        // ... código de layout ...
        
        pack();
    }
    
    // EVENTO: Botón Salir
    private void SalirActionPerformed(java.awt.event.ActionEvent evt) {
        System.exit(0);  // Cierra la aplicación
    }
    
    // EVENTO: Botón Convertir
    private void convertirActionPerformed(java.awt.event.ActionEvent evt) {
        // 1. Obtener el valor en litros
        String a = resultado.getText();
        
        // 2. Convertir de String a int
        int c = Integer.parseInt(a);
        
        // 3. Variable para almacenar el resultado
        float resultadoConversion = 0;
        
        // 4. Determinar qué unidad fue seleccionada y convertir
        if (ml.isSelected()) {
            // 1 litro = 1000 mililitros
            resultadoConversion = (float) c * 1000;
        } else if (galon.isSelected()) {
            // 1 litro = 0.264 galones (1 galón = 3.785 litros)
            resultadoConversion = (float) (c / 3.785);
        } else if (oz.isSelected()) {
            // 1 litro = 33.814 onzas
            resultadoConversion = (float) (c * 33.814);
        } else if (m3.isSelected()) {
            // 1 litro = 0.001 metros cúbicos
            resultadoConversion = (float) c / 1000;
        }
        
        // 5. Mostrar el resultado
        resul.setText(String.valueOf(resultadoConversion));
    }
    
    public static void main(String args[]) {
        java.awt.EventQueue.invokeLater(new Runnable() {
            public void run() {
                new conversiones().setVisible(true);
            }
        });
    }
}
```

#### Análisis Detallado del Método convertirActionPerformed

Este es el corazón del programa. Vamos línea por línea:

**Paso 1: Obtener el texto del campo de entrada**
```java
String a = resultado.getText();
```
- `resultado` es el JTextField donde el usuario escribe los litros
- `getText()` obtiene el texto como String
- Ejemplo: si el usuario escribió "5", `a` = "5"

**Paso 2: Convertir String a número**
```java
int c = Integer.parseInt(a);
```
- `Integer.parseInt()` convierte String a int
- Ejemplo: `"5"` → `5`
- ⚠️ Si el usuario escribe texto no numérico, lanza excepción

**Paso 3: Variable para almacenar resultado**
```java
float resultadoConversion = 0;
```
- `float` permite decimales (3.14, 2.5, etc.)
- Inicializado en 0

**Paso 4: Estructura if-else if para detectar unidad seleccionada**
```java
if (ml.isSelected()) {
    resultadoConversion = (float) c * 1000;
}
```
- `ml.isSelected()` retorna `true` si el radio button "Mililitros" está seleccionado
- `(float) c` convierte el int a float (cast)
- `* 1000` multiplica por 1000 (1 litro = 1000 ml)

**Fórmulas de conversión:**

| De Litros a: | Fórmula | Ejemplo (5 litros) |
|--------------|---------|---------------------|
| Mililitros   | L × 1000 | 5 × 1000 = 5000 ml |
| Galones      | L ÷ 3.785 | 5 ÷ 3.785 = 1.32 gal |
| Onzas        | L × 33.814 | 5 × 33.814 = 169.07 oz |
| Metros cúbicos | L ÷ 1000 | 5 ÷ 1000 = 0.005 m³ |

**Paso 5: Mostrar resultado**
```java
resul.setText(String.valueOf(resultadoConversion));
```
- `String.valueOf()` convierte el número a String
- `setText()` muestra el resultado en la etiqueta `resul`

#### Conceptos Importantes

**1. Casting (Conversión de tipos)**

```java
int entero = 5;
float decimal = (float) entero;  // 5.0

// También:
float resultado = (float) (entero / 3.785);
```

**¿Por qué usar casting?**
```java
int a = 5;
int b = 2;
int resultado = a / b;    // resultado = 2 (división entera)

float resultado2 = (float) a / b;  // resultado2 = 2.5 (división decimal)
```

**2. Tipos de datos numéricos**

| Tipo | Tamaño | Rango | Decimales | Uso |
|------|--------|-------|-----------|-----|
| `byte` | 8 bits | -128 a 127 | No | Números muy pequeños |
| `short` | 16 bits | -32,768 a 32,767 | No | Números pequeños |
| `int` | 32 bits | -2 mil millones a 2 mil millones | No | **Enteros normales** |
| `long` | 64 bits | Muy grande | No | Enteros enormes |
| `float` | 32 bits | ±3.4e38 | Sí (7 dígitos) | **Decimales normales** |
| `double` | 64 bits | ±1.7e308 | Sí (15 dígitos) | Decimales precisos |

**3. System.exit(0)**

```java
System.exit(0);
```
- Termina completamente la aplicación Java
- `0` indica salida normal
- Números diferentes indican errores

**4. EventQueue.invokeLater()**

```java
java.awt.EventQueue.invokeLater(new Runnable() {
    public void run() {
        new conversiones().setVisible(true);
    }
});
```

- **EDT (Event Dispatch Thread):** Hilo especial para interfaces gráficas
- `invokeLater()` asegura que la GUI se cree en el hilo correcto
- Previene problemas de concurrencia
- Es la forma **recomendada** de iniciar aplicaciones Swing

**Versión simplificada con lambda:**
```java
java.awt.EventQueue.invokeLater(() -> {
    new conversiones().setVisible(true);
});
```

#### Flujo del Programa

```
┌─────────────────────────┐
│ Usuario abre programa   │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ Ventana se muestra      │
│ - Campo "Litros" vacío  │
│ - Radio buttons         │
│ - Botones               │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ Usuario ingresa número  │
│ en campo "Litros"       │
│ Ejemplo: "5"            │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ Usuario selecciona      │
│ unidad (radio button)   │
│ Ejemplo: Mililitros     │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ Usuario hace clic en    │
│ "Convertir"             │
└───────────┬─────────────┘
            │
            ▼
┌─────────────────────────┐
│ convertirActionPerformed│
│ 1. Lee "5"              │
│ 2. Convierte a int: 5   │
│ 3. Detecta ML           │
│ 4. Calcula: 5 × 1000    │
│ 5. Muestra: 5000        │
└─────────────────────────┘
```

#### Errores Comunes y Soluciones

**Error 1: NumberFormatException**

```java
// ❌ Problema: Usuario escribe "abc"
String texto = "abc";
int numero = Integer.parseInt(texto);  // ¡CRASH!

// ✅ Solución: Try-Catch
try {
    int numero = Integer.parseInt(texto);
    // Usar numero...
} catch (NumberFormatException e) {
    JOptionPane.showMessageDialog(null, 
        "Por favor ingrese solo números");
}
```

**Error 2: División por cero**

```java
// ❌ Problema
int resultado = 5 / 0;  // ¡ArithmeticException!

// ✅ Solución
if (divisor != 0) {
    int resultado = dividendo / divisor;
} else {
    System.out.println("No se puede dividir por cero");
}
```

**Error 3: Ningún radio button seleccionado**

```java
// ❌ Problema: resultado = 0 si ninguno está seleccionado

// ✅ Solución
if (!ml.isSelected() && !galon.isSelected() && 
    !oz.isSelected() && !m3.isSelected()) {
    JOptionPane.showMessageDialog(null, 
        "Por favor seleccione una unidad");
    return;  // Sale del método
}
```

#### Versión Mejorada con Validación

```java
private void convertirActionPerformed(ActionEvent evt) {
    try {
        // Validar que el campo no esté vacío
        String texto = resultado.getText().trim();
        if (texto.isEmpty()) {
            JOptionPane.showMessageDialog(this, 
                "Por favor ingrese un valor en litros", 
                "Campo vacío", 
                JOptionPane.WARNING_MESSAGE);
            return;
        }
        
        // Convertir a número
        float litros = Float.parseFloat(texto);
        
        // Validar que sea positivo
        if (litros < 0) {
            JOptionPane.showMessageDialog(this, 
                "El valor debe ser positivo", 
                "Valor inválido", 
                JOptionPane.ERROR_MESSAGE);
            return;
        }
        
        // Validar que se haya seleccionado una unidad
        if (!ml.isSelected() && !galon.isSelected() && 
            !oz.isSelected() && !m3.isSelected()) {
            JOptionPane.showMessageDialog(this, 
                "Por favor seleccione una unidad de conversión", 
                "Selección requerida", 
                JOptionPane.WARNING_MESSAGE);
            return;
        }
        
        // Realizar conversión
        float resultadoConversion = 0;
        String unidad = "";
        
        if (ml.isSelected()) {
            resultadoConversion = litros * 1000;
            unidad = "ml";
        } else if (galon.isSelected()) {
            resultadoConversion = litros / 3.785f;
            unidad = "gal";
        } else if (oz.isSelected()) {
            resultadoConversion = litros * 33.814f;
            unidad = "oz";
        } else if (m3.isSelected()) {
            resultadoConversion = litros / 1000;
            unidad = "m³";
        }
        
        // Formatear resultado a 2 decimales
        String resultadoFormateado = String.format("%.2f %s", 
            resultadoConversion, unidad);
        resul.setText(resultadoFormateado);
        
    } catch (NumberFormatException e) {
        JOptionPane.showMessageDialog(this, 
            "Por favor ingrese un número válido", 
            "Error de formato", 
            JOptionPane.ERROR_MESSAGE);
    }
}
```

**Nuevos conceptos en la versión mejorada:**

1. **trim():** Elimina espacios al inicio y final
   ```java
   "  5  ".trim()  // "5"
   ```

2. **isEmpty():** Verifica si el string está vacío
   ```java
   "".isEmpty()     // true
   "abc".isEmpty()  // false
   ```

3. **String.format():** Formatea números
   ```java
   String.format("%.2f", 3.14159)  // "3.14"
   String.format("%.2f", 5.0)      // "5.00"
   ```

4. **Literales float:** Agregar `f` al final
   ```java
   float x = 3.785f;  // Literal float
   float y = 3.785;   // Double convertido a float
   ```

#### Ejercicio Propuesto

Crea un conversor de temperatura que convierta entre:
- Celsius a Fahrenheit: F = (C × 9/5) + 32
- Celsius a Kelvin: K = C + 273.15
- Fahrenheit a Celsius: C = (F - 32) × 5/9

Requisitos:
1. Campo de entrada
2. Radio buttons para seleccionar conversión
3. Validación de entrada
4. Mostrar resultado con 2 decimales

---


## RESUMEN DE CONCEPTOS CLAVE

### Conceptos Fundamentales de Java Swing

#### 1. Jerarquía de Componentes
```
JComponent (clase base abstracta)
    ├── JLabel (etiquetas de texto/imágenes)
    ├── JButton (botones clicables)
    ├── AbstractButton
    │   ├── JRadioButton (selección única)
    │   ├── JCheckBox (selección múltiple)
    │   └── JToggleButton
    ├── JTextField (entrada de texto una línea)
    ├── JTextArea (entrada de texto multilínea)
    ├── JPanel (contenedor para organizar componentes)
    └── JScrollPane (panel con barras de desplazamiento)

Container (nivel superior)
    ├── JFrame (ventana principal)
    ├── JDialog (ventana de diálogo)
    └── JWindow (ventana sin bordes)
```

#### 2. Ciclo de Vida de una Aplicación Swing

```
┌─────────────────────────────────────────────┐
│ 1. Crear JFrame                             │
│    JFrame frame = new JFrame();             │
└──────────────┬──────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────┐
│ 2. Configurar propiedades                   │
│    - setTitle()                             │
│    - setSize() o setBounds()                │
│    - setDefaultCloseOperation()             │
│    - setLayout()                            │
└──────────────┬──────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────┐
│ 3. Crear componentes                        │
│    - JLabel, JButton, JTextField, etc.      │
└──────────────┬──────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────┐
│ 4. Configurar componentes                   │
│    - setText(), setFont(), setForeground()  │
│    - setBounds() (si layout es null)        │
└──────────────┬──────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────┐
│ 5. Agregar listeners (eventos)              │
│    - addActionListener()                    │
└──────────────┬──────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────┐
│ 6. Agregar componentes al frame             │
│    - add(componente)                        │
└──────────────┬──────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────┐
│ 7. Hacer visible                            │
│    - setVisible(true)                       │
└──────────────┬──────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────┐
│ 8. Programa corriendo                       │
│    - Escuchando eventos                     │
│    - Respondiendo a interacciones           │
└─────────────────────────────────────────────┘
```

### Cheat Sheet de Métodos Esenciales

#### JFrame
```java
setTitle(String)               // Título de la ventana
setSize(int width, int height) // Tamaño
setBounds(int x, int y, int w, int h) // Posición y tamaño
setVisible(boolean)            // Mostrar/ocultar
setDefaultCloseOperation(int)  // Acción al cerrar
setResizable(boolean)          // Permitir redimensionar
setLocationRelativeTo(null)    // Centrar en pantalla
setLayout(LayoutManager)       // Establecer layout
add(Component)                 // Agregar componente
pack()                         // Ajustar tamaño automático
```

#### JLabel
```java
setText(String)                // Cambiar texto
getText()                      // Obtener texto
setFont(Font)                  // Cambiar fuente
setForeground(Color)           // Color de texto
setBackground(Color)           // Color de fondo
setOpaque(true)                // Hacer visible el fondo
setHorizontalAlignment(int)    // Alineación
setIcon(Icon)                  // Agregar imagen
```

#### JTextField
```java
setText(String)                // Establecer texto
getText()                      // Obtener texto
setEditable(boolean)           // Permitir editar
setColumns(int)                // Ancho en columnas
selectAll()                    // Seleccionar todo
```

#### JButton
```java
setText(String)                // Texto del botón
setEnabled(boolean)            // Activar/desactivar
addActionListener(ActionListener) // Agregar evento
setBackground(Color)           // Color de fondo
setForeground(Color)           // Color de texto
```

#### JRadioButton
```java
isSelected()                   // ¿Está seleccionado?
setSelected(boolean)           // Seleccionar
getText()                      // Obtener texto
// IMPORTANTE: Debe estar en un ButtonGroup
```

#### JCheckBox
```java
isSelected()                   // ¿Está marcado?
setSelected(boolean)           // Marcar/desmarcar
getText()                      // Obtener texto
// NO necesita ButtonGroup
```

### Conversiones de Tipos de Datos

```java
// String → Número
int num1 = Integer.parseInt("123");
double num2 = Double.parseDouble("3.14");
float num3 = Float.parseFloat("2.5");

// Número → String
String str1 = String.valueOf(123);
String str2 = Integer.toString(123);
String str3 = "" + 123;  // Concatenación automática

// Con formato
String formatted = String.format("%.2f", 3.14159); // "3.14"

// Casting
int a = 5;
float b = (float) a;     // int → float
double c = a;            // Conversión automática
int d = (int) 3.14;      // double → int (se pierde decimal)
```

### Manejo de Eventos - Resumen

#### Opción 1: Implementar ActionListener
```java
public class MiVentana extends JFrame implements ActionListener {
    private JButton boton;
    
    public MiVentana() {
        boton = new JButton("Click");
        boton.addActionListener(this);  // "this" = esta clase
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        // Código del evento
    }
}
```

#### Opción 2: Clase Anónima
```java
boton.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        // Código del evento
    }
});
```

#### Opción 3: Lambda (Recomendada)
```java
boton.addActionListener(e -> {
    // Código del evento
});
```

### Colores Comunes

```java
Color.RED          // Rojo
Color.BLUE         // Azul
Color.GREEN        // Verde
Color.YELLOW       // Amarillo
Color.BLACK        // Negro
Color.WHITE        // Blanco
Color.GRAY         // Gris
Color.ORANGE       // Naranja
Color.PINK         // Rosa

// Color personalizado RGB (0-255)
new Color(255, 0, 0)     // Rojo
new Color(0, 255, 0)     // Verde
new Color(0, 0, 255)     // Azul
new Color(128, 128, 128) // Gris medio
```

### Fuentes Comunes

```java
// Font(nombre, estilo, tamaño)
new Font("Arial", Font.PLAIN, 12)
new Font("Arial", Font.BOLD, 14)
new Font("Arial", Font.ITALIC, 12)
new Font("Arial", Font.BOLD | Font.ITALIC, 14)

// Fuentes comunes
"Arial"
"Times New Roman"
"Courier New"
"Verdana"
"Tahoma"
```

### Errores Comunes y Soluciones

#### 1. Ventana no aparece
```java
// ❌ Problema: Olvidaste setVisible
JFrame frame = new JFrame();
frame.setSize(400, 300);
// frame.setVisible(true);  // FALTA ESTO

// ✅ Solución
frame.setVisible(true);
```

#### 2. Programa no cierra al cerrar ventana
```java
// ❌ Problema: Falta setDefaultCloseOperation
JFrame frame = new JFrame();

// ✅ Solución
frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
```

#### 3. Componentes no se ven
```java
// ❌ Problema: Olvidaste add()
JButton boton = new JButton("Click");
// add(boton);  // FALTA ESTO

// ✅ Solución
add(boton);
```

#### 4. NullPointerException
```java
// ❌ Problema: Usar componente antes de crearlo
private JLabel label;

public MiVentana() {
    label.setText("Hola");  // ¡CRASH! label es null
}

// ✅ Solución
private JLabel label;

public MiVentana() {
    label = new JLabel();  // Crear primero
    label.setText("Hola"); // Luego usar
}
```

#### 5. NumberFormatException
```java
// ❌ Problema: Convertir texto no numérico
String texto = "abc";
int numero = Integer.parseInt(texto);  // ¡CRASH!

// ✅ Solución
try {
    int numero = Integer.parseInt(texto);
} catch (NumberFormatException e) {
    JOptionPane.showMessageDialog(null, "Ingrese un número válido");
}
```

### Mejores Prácticas

1. **Orden de inicialización:**
   - Configurar frame
   - Crear componentes
   - Configurar componentes
   - Agregar listeners
   - Agregar a frame
   - setVisible(true) AL FINAL

2. **Nombres de variables descriptivos:**
   ```java
   // ❌ Mal
   JButton b1, b2;
   JLabel l1;
   
   // ✅ Bien
   JButton btnCalcular, btnLimpiar;
   JLabel lblResultado;
   ```

3. **Validar entradas del usuario:**
   ```java
   String texto = txtNumero.getText().trim();
   if (texto.isEmpty()) {
       JOptionPane.showMessageDialog(this, "Campo vacío");
       return;
   }
   ```

4. **Separar lógica de interfaz:**
   ```java
   // Método para cálculo (lógica)
   private double calcular(double a, double b) {
       return a + b;
   }
   
   // Método de evento (interfaz)
   private void btnCalcularClick(ActionEvent e) {
       double num1 = Double.parseDouble(txt1.getText());
       double num2 = Double.parseDouble(txt2.getText());
       double resultado = calcular(num1, num2);
       lblResultado.setText(String.valueOf(resultado));
   }
   ```

5. **Usar constantes:**
   ```java
   private static final int ANCHO_VENTANA = 400;
   private static final int ALTO_VENTANA = 300;
   private static final Color COLOR_FONDO = new Color(240, 240, 240);
   
   setSize(ANCHO_VENTANA, ALTO_VENTANA);
   getContentPane().setBackground(COLOR_FONDO);
   ```

---

## GLOSARIO DE TÉRMINOS

**API (Application Programming Interface):** Conjunto de clases y métodos que proporciona Java para crear programas.

**AWT (Abstract Window Toolkit):** Biblioteca antigua de Java para GUIs. Swing se construyó sobre AWT.

**Cast/Casting:** Convertir un tipo de dato a otro, por ejemplo: `(int) 3.14` convierte double a int.

**Component:** Cualquier elemento visual de la interfaz (botón, etiqueta, campo de texto, etc.)

**Constructor:** Método especial que se ejecuta al crear un objeto. Tiene el mismo nombre que la clase.

**Container:** Componente que puede contener otros componentes (JFrame, JPanel, etc.)

**EDT (Event Dispatch Thread):** Hilo especial de Java donde se ejecutan las operaciones de la GUI.

**Event:** Acción del usuario (clic, tecla presionada, mouse movido, etc.)

**Herencia:** Cuando una clase "hereda" características de otra usando `extends`.

**IDE (Integrated Development Environment):** Programa para escribir código (NetBeans, Eclipse, IntelliJ).

**Instancia:** Un objeto específico creado de una clase.

**Interface:** Contrato que especifica qué métodos debe implementar una clase.

**JFC (Java Foundation Classes):** Conjunto de bibliotecas que incluyen Swing.

**Layout Manager:** Objeto que controla cómo se posicionan los componentes en un contenedor.

**Listener:** Objeto que "escucha" eventos y ejecuta código cuando ocurren.

**Method Overriding:** Sobrescribir un método de la clase padre en la clase hija.

**Null:** Valor especial que indica que una variable no apunta a ningún objeto.

**Package:** Carpeta que agrupa clases relacionadas.

**Swing:** Biblioteca de Java para crear interfaces gráficas modernas.

**Variable de Instancia:** Variable declarada en la clase, fuera de los métodos. Pertenece al objeto.

**Variable Local:** Variable declarada dentro de un método. Solo existe en ese método.

---

## RECURSOS ADICIONALES

### Documentación Oficial
- Oracle Java Documentation: https://docs.oracle.com/javase/tutorial/uiswing/
- Java Swing API: https://docs.oracle.com/javase/8/docs/api/javax/swing/package-summary.html

### Tutoriales Recomendados
- JavaTpoint Swing: https://www.javatpoint.com/java-swing
- GeeksforGeeks Swing: https://www.geeksforgeeks.org/introduction-to-java-swing/
- Tutorialspoint Swing: https://www.tutorialspoint.com/swing/index.htm

### Videos y Cursos
- Buscar en YouTube: "Java Swing tutorial español"
- Cursos en Udemy sobre Java GUI
- Tutoriales en español en YouTube

### Práctica
- Crea mini-proyectos:
  - Calculadora científica
  - Conversor de monedas
  - Lista de tareas (To-Do List)
  - Formulario de registro
  - Juego simple (piedra, papel, tijera)

---

## PROYECTOS SUGERIDOS PARA PRACTICAR

### Proyecto 1: Calculadora Científica
**Dificultad:** Media  
**Conceptos:** Botones, eventos, operaciones matemáticas  
**Componentes:** JFrame, JButton, JTextField, JPanel  
**Funciones:** +, -, ×, ÷, √, x², sin, cos, tan

### Proyecto 2: Sistema de Login
**Dificultad:** Básica  
**Conceptos:** JPasswordField, validación, comparación de strings  
**Componentes:** JFrame, JTextField, JPasswordField, JButton, JLabel  
**Características:** Verificar usuario y contraseña, mensajes de error

### Proyecto 3: Conversor Universal
**Dificultad:** Media  
**Conceptos:** Radio buttons, combo box, múltiples conversiones  
**Conversiones:** 
- Temperatura (C, F, K)
- Longitud (m, km, mi, ft)
- Peso (kg, lb, oz)
- Moneda (USD, EUR, MXN)

### Proyecto 4: Quiz Interactivo
**Dificultad:** Media-Alta  
**Conceptos:** Arrays, lógica condicional, puntuación  
**Componentes:** JRadioButton, JButton, JLabel, JProgressBar  
**Características:** Preguntas múltiple opción, puntaje, retroalimentación

### Proyecto 5: Editor de Texto Básico
**Dificultad:** Alta  
**Conceptos:** JTextArea, JMenuBar, manejo de archivos  
**Componentes:** JFrame, JTextArea, JScrollPane, JMenuBar, JFileChooser  
**Funciones:** Abrir, guardar, copiar, pegar, buscar

---

## PALABRAS FINALES

Has completado un recorrido extenso por Java Swing y las interfaces gráficas. Los conceptos aprendidos son fundamentales para:

✅ Crear aplicaciones de escritorio profesionales  
✅ Entender cómo funcionan las interfaces gráficas  
✅ Manejar eventos y la interacción con el usuario  
✅ Validar datos y prevenir errores  
✅ Organizar código de manera eficiente  

**Próximos pasos:**

1. **Practica constantemente:** Haz los ejercicios propuestos
2. **Modifica los ejemplos:** Experimenta con el código
3. **Crea proyectos personales:** Aplica lo aprendido
4. **Lee código de otros:** Aprende diferentes estilos
5. **Investiga conceptos avanzados:** JTable, JTree, MVC, etc.

**Recuerda:**
> "La programación se aprende programando, no solo leyendo."

¡Sigue practicando y creando! 🚀

---

**Fin de los Apuntes**

---

© 2026 - Apuntes Completos de Tópicos de Programación  
Elaborado con análisis detallado y ejemplos prácticos

