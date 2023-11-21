# calculadora-electronica
Proyecto final de electricidad 2, calculadora que permite el calculo de impedancias y de filtros pasivos 
import cmath
import math
import tkinter as tk
from tkinter import messagebox, Label, Entry, Button, Frame

# Calculadora de Impedancia
def calcular_impedancia():
    R = float(resistencia.get())
    L = float(inductancia.get())
    C = float(capacitancia.get())
    f = float(frecuencia.get())
    w = 2 * math.pi * f
    Z_R = R  
    Z_L = complex(0, w * L)  
    Z_C = complex(0, -1 / (w * C)) if C != 0 else float('inf')
    if circuito.get() == "Serie":
        Z_total = Z_R + Z_L + Z_C  #circuito en serie
    else:  # Paralelo
        if Z_C == float('inf'): 
            Z_total = min(Z_R, Z_L)
        else:
            Z_total = 1 / (1/Z_R + 1/Z_L + 1/Z_C)  #circuito en paralelo
    messagebox.showinfo("Resultado", f"Impedancia total: {Z_total}")

#Calculadora de Filtros Pasivos
def calcular_resistencia():
    f = float(frecuencia_filtros.get())
    C = float(capacitancia_filtros.get())
    R = 1 / (2 * math.pi * f * C)
    messagebox.showinfo("Resultado", f"Resistencia: {R}")

def calcular_frecuencia():
    R = float(resistencia_filtros.get())
    C = float(capacitancia_filtros.get())
    f = 1 / (2 * math.pi * R * C)
    messagebox.showinfo("Resultado", f"Frecuencia: {f}")

def calcular_capacitor():
    R = float(resistencia_filtros.get())
    f = float(frecuencia_filtros.get())
    C = 1 / (2 * math.pi * f * R)
    messagebox.showinfo("Resultado", f"Capacitor: {C}")

def calcular_respuesta():
    R = float(resistencia_filtros.get())
    C = float(capacitancia_filtros.get())
    f = float(frecuencia_filtros.get())
    w = 2 * math.pi * f
    Z_R = R  
    Z_C = complex(0, -1 / (w * C)) if C != 0 else float('inf') 
    if tipo_filtro.get() == "Pasa Bajos":
        H = 1 / (Z_R + Z_C)  #filtro pasa bajos
    else:  # Pasa Altos
        H = Z_C / (Z_R + Z_C)  #filtro pasa altos
    magnitud = abs(H)
    fase = cmath.phase(H)
    messagebox.showinfo("Resultado", f"Magnitud: {magnitud}, Fase: {fase}")

root = tk.Tk()
root.title("Calculadora de Circuitos")

resistencia = Entry(root)
inductancia = Entry(root)
capacitancia = Entry(root)
frecuencia = Entry(root)
circuito = tk.StringVar(root)
circuito.set("Serie")  
tipo_circuito = tk.OptionMenu(root, circuito, "Serie", "Paralelo")

resistencia_filtros = Entry(root)
capacitancia_filtros = Entry(root)
frecuencia_filtros = Entry(root)
tipo_filtro = tk.StringVar(root)
tipo_filtro.set("Pasa Bajos")  
tipo_filtro_menu = tk.OptionMenu(root, tipo_filtro, "Pasa Bajos", "Pasa Altos")

btn_impedancia = Button(root, text="Calcular Impedancia", command=calcular_impedancia)
btn_resistencia = Button(root, text="Calcular Resistencia", command=calcular_resistencia)
btn_frecuencia = Button(root, text="Calcular Frecuencia", command=calcular_frecuencia)
btn_capacitor = Button(root, text="Calcular Capacitor", command=calcular_capacitor)
btn_respuesta = Button(root, text="Calcular Respuesta del Filtro", command=calcular_respuesta)

frame_impedancia = Frame(root, borderwidth=2, relief="groove")
frame_filtros = Frame(root, borderwidth=2, relief="groove")

# Colocar los widgets en la ventana
Label(frame_impedancia, text="Calculadora de Impedancia").pack()
Label(frame_impedancia, text="Resistencia (R):").pack()
resistencia.pack()
Label(frame_impedancia, text="Inductancia (L):").pack()
inductancia.pack()
Label(frame_impedancia, text="Capacitancia (C):").pack()
capacitancia.pack()
Label(frame_impedancia, text="Frecuencia (f):").pack()
frecuencia.pack()
Label(frame_impedancia, text="Tipo de Circuito:").pack()
tipo_circuito.pack()
btn_impedancia.pack()

Label(frame_filtros, text="Calculadora de Filtros Pasivos").pack()
Label(frame_filtros, text="Resistencia (R):").pack()
resistencia_filtros.pack()
Label(frame_filtros, text="Capacitancia (C):").pack()
capacitancia_filtros.pack()
Label(frame_filtros, text="Frecuencia (f):").pack()
frecuencia_filtros.pack()
Label(frame_filtros, text="Tipo de Filtro:").pack()
tipo_filtro_menu.pack()
btn_resistencia.pack()
btn_frecuencia.pack()
btn_capacitor.pack()
btn_respuesta.pack()

frame_impedancia.pack(side="left", padx=10, pady=10, fill="both")
frame_filtros.pack(side="right", padx=10, pady=10, fill="both")

root.mainloop()
