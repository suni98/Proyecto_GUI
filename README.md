# Proyecto_GUI
import tkinter as tk
from tkinter import messagebox

# Función para agregar datos a la tabla
def agregar_dato():
    dato = entrada_dato.get()
    if dato:
        tabla_datos.insert(tk.END, f"{dato}\n")
        entrada_dato.delete(0, tk.END)  # Limpiar el campo de texto
    else:
        messagebox.showwarning("Advertencia", "El campo de texto está vacío.")

# Función para limpiar la tabla de datos
def limpiar_tabla():
    tabla_datos.delete('1.0', tk.END)

# Crear la ventana principal
ventana = tk.Tk()
ventana.title("Aplicación GUI Básica con Tabla")

# Crear un frame para organizar los elementos
frame = tk.Frame(ventana)
frame.pack(pady=20, padx=20)

# Crear y organizar los componentes GUI
label_titulo = tk.Label(frame, text="Ingrese un dato:")
label_titulo.grid(row=0, column=0, pady=5)

entrada_dato = tk.Entry(frame, width=40)
entrada_dato.grid(row=0, column=1, pady=5, padx=10)

boton_agregar = tk.Button(frame, text="Agregar", command=agregar_dato)
boton_agregar.grid(row=0, column=2, padx=10)

# Crear una tabla simulada usando el widget Text
label_tabla = tk.Label(frame, text="Datos ingresados:")
label_tabla.grid(row=1, column=0, columnspan=3)

tabla_datos = tk.Text(frame, width=50, height=10, state='normal')
tabla_datos.grid(row=2, column=0, columnspan=3, pady=10)

boton_limpiar = tk.Button(frame, text="Limpiar Tabla", command=limpiar_tabla)
boton_limpiar.grid(row=3, column=0, columnspan=3, pady=10)

# Iniciar el bucle principal de la ventana
ventana.mainloop()
