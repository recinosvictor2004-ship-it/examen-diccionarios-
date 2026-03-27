games = {
    "The Witcher 3": 9.5,
    "Minecraft": 9.0,
    "Celeste": 8.7
}

def add_game(name, score):
    """
    Agrega un nuevo juego o actualiza su puntuación.
    name: nombre del juego (str)
    score: puntuación entre 0 y 10 (float)
    """
    if 0 <= score <= 10:
        games[name] = score
        print(f"'{name}' registrado/actualizado con puntuación {score}")
    else:
        print(" La puntuación debe estar entre 0 y 10.")

def top_n(n):
    """
    Devuelve una lista de tuplas (juego, puntuación)
    con los n juegos mejor valorados.
    """
    # Ordenar por puntuación descendente
    sorted_games = sorted(games.items(), key=lambda x: x[1], reverse=True)
    return sorted_games[:n]

def listar_juegos():
    """Muestra todos los juegos registrados."""
    if not games:
        print("No hay juegos registrados.")
        return
    print("\n Lista de juegos:")
    for name, score in games.items():
        print(f" - {name}: {score}")

def menu():
    while True:
        print("\n===== MENÚ PRINCIPAL =====")
        print("1. Listar todos los juegos")
        print("2. Añadir o actualizar un juego")
        print("3. Mostrar Top 3")
        print("4. Salir")

        opcion = input("Seleccione una opción: ")

        if opcion == "1":
            listar_juegos()

        elif opcion == "2":
            name = input("Nombre del juego: ")
            try:
                score = float(input("Puntuación (0–10): "))
                add_game(name, score)
            except ValueError:
                print(" Debes ingresar un número válido.")

        elif opcion == "3":
            top3 = top_n(3)
            print("\n Top 3 Juegos Mejor Valorados:")
            for i, (name, score) in enumerate(top3, start=1):
                print(f"{i}. {name} — {score}")

        elif opcion == "4":
            print("Saliendo del programa...")
            break

        else:
            print(" Opción no válida. Intente de nuevo.")


menu()
