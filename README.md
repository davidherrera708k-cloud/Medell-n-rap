import random
import time
import os

def clear():
    os.system('cls' if os.name == 'nt' else 'clear')

class Jugador:
    def __init__(self, nombre, apodo):
        self.nombre = nombre
        self.apodo = apodo
        self.edad = 14
        self.dia = 1
        self.mes = 1
        self.anio = 2010
        self.dinero = 25000
        self.fama = 0
        self.energia = 100
        self.rap = 12
        self.prod = 8
        self.respeto = 3
        self.estilo = "Callejero"
        self.canciones = []
        self.beats = 0
        self.vehiculo = "A pie"
        self.plataformas = ["YouTube", "SoundCloud", "TikTok", "Instagram"]

    def mostrar(self):
        print("\n" + "="*50)
        print(f"  {self.apodo} ({self.nombre}) - {self.edad} años")
        print(f"  {self.dia}/{self.mes}/{self.anio} | {self.estilo}")
        print("="*50)
        print(f"  Dinero: ${self.dinero:,} COP")
        print(f"  Fama: {self.fama}/1000")
        print(f"  Energía: {self.energia}/100")
        print(f"  Rap: {self.rap}/100 | Producción: {self.prod}/100")
        print(f"  Respeto: {self.respeto} | Vehículo: {self.vehiculo}")
        print("="*50)

    def avanzar(self, dias=1):
        self.dia += dias
        while self.dia > 30:
            self.dia -= 30
            self.mes += 1
            if self.mes > 12:
                self.mes = 1
                self.anio += 1
                self.edad += 1
        self.energia = min(100, self.energia + dias * 7)
        if self.fama > 5 and random.random() < 0.25:
            self.fama = max(0, self.fama - random.randint(1, 2))


def crear_personaje():
    clear()
    print("="*50)
    print("       CALLEJERO DE MEDELLÍN")
    print("   Desde los 14 años soñando con el mic")
    print("="*50)
    nombre = input("\nNombre completo: ").strip() or "Juan Camilo"
    apodo = input("Nombre artístico: ").strip() or "El Ladero"
    print(f"\nBienvenido a la calle, {apodo}...")
    time.sleep(1)
    return Jugador(nombre, apodo)


def crear_cancion(j):
    if j.energia < 12:
        print("\nNo tienes suficiente energía (mínimo 12).")
        return
    print("\n--- CREAR CANCIÓN ---")
    titulo = input("Título de la canción: ").strip() or "Sin título"
    
    print("\nEstilos: 1.Trap Medellín  2.Boom Bap  3.Drill  4.Old School  5.Melódico")
    estilo = ["Trap Medellín","Boom Bap","Drill","Old School","Melódico"][max(0, min(4, int(input("Elige (1-5): ") or 1)-1))]
    
    print("\n¿Qué