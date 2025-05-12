# ccc
inventary = [] # List to store inventory products

# Function to validate numeric inputs
def number_invalid (mesanje, numero):
    while True:
        entrace = input(mesanje).strip()
        try:
            return float(entrace)
        except ValueError:
            print("Ingrese un numero valido")



# Function to add a product to inventory
def enter_product():
    name = input("Ingresa el nombre del producto: ").strip() .lower()
    price = number_invalid("Precio del producto: $")
    amount = number_invalid("Ingrese la cantidad de productos: ")


    product = { 'name': name, 'price' : price, "amount" : amount  }
    inventary.append(product)
    print(f"El producto {name} fue añadido")    

# Function to search for a product by name
def consult_product (name):
    for i in inventary:
                if i['name'] == name :
                    return i
    return None

# Function to update the price of a product
def update_price ():
    name = input("Nombre del producto a actualizar: ").strip().lower()
    product = consult_product(name)
    if product:
        new_price = number_invalid("Nuevo precio: ")
        product['price'] = new_price
        print("Precio actualizado.")
    else:
        print("Producto no encontrado.")

# Function to remove a product from inventory
def delete_product():
    name = input("Nombre del producto a eliminar: ").strip().lower()
    producto = consult_product(name)
    if producto:
        inventary.remove(producto)
        print(f"El producto {name} fue eliminado del inventario.")
    else:
        print("Producto no encontrado en el inventario.")


# Lambda function to calculate the total value of inventory
calculate_total_value = lambda: sum(p['price'] * p['amount'] for p in inventary)

# Function to display all products
def see_product():
    if not inventary:
        print(" El inventario está vacío.")
    else:
        print("\n Productos en inventario:")
        print("{:<20} {:>10} {:>10}".format("Nombre", "Precio", "Cantidad"))
        print("-" * 42)
        for i in inventary:
            nombre = i  ["name"]
            precio = f"${i["price"]:.2f}"
            cantidad = f"{i["amount"]:.0f}" if i["amount"] else f"{i["amount"]}"
            print( "{:<20} {:>10} {:>10}".format(nombre, precio, cantidad))
        
# Bucle program main
def menu():
    while True:
        print("""
-----------------------------------------------
|          Bienvenido al inventario           |
|---------------------------------------------|
|      1. Añadir producto al inventario       |
|      2. Consultar producto en el inventario |
|      3. Actualizar precio del producto      |
|      4. Eliminar producto del inventario    |
|      5. Valor total del inventario          |           
|      6. Mostrar productos en inventario     |     
|      7. Salir                               |
-----------------------------------------------""")
        
        # Enter the required option
        option = input("Seleccione el numero del requerimiento que desea utilizar: ").strip()
        
        # If this option is, it will be executed
        if option == "1":
            enter_product()
        elif option == "2":
            nombre = input("Nombre del producto a buscar: ").strip().lower()
            producto = consult_product(nombre)
            if producto:
                print(f"Producto: {producto['name']}, Precio: {producto['price']}, Cantidad: {producto['amount']}")
            else:
                print("Producto no encontrado.")
        elif option == "3":
            update_price()
        elif option == "4":
            delete_product()
        elif option == "5":
            total = calculate_total_value()
            print(f" Valor total del inventario: ${total:.2f}")
        elif option == "6":
            see_product()
        elif option == "7":
            print("Saliendo del programa.")
            break
        else:
            print("Opción no válida. Intente nuevamente.")
        
# Entry point
if __name__ == "__main__":
    menu()



----------------------------


inventary = []  # Lista para almacenar productos

# Función para validar entradas numéricas no negativas
def number_invalid(mensaje):
    while True:
        entrada = input(mensaje).strip()
        try:
            numero = float(entrada)
            if numero < 0:
                print("No se permiten números negativos.")
            else:
                return numero
        except ValueError:
            print("Ingrese un número válido.")

# Función para añadir un producto al inventario
def enter_product():
    name = input("Ingresa el nombre del producto: ").strip().lower()
    price = number_invalid("Precio del producto: $")
    amount = number_invalid("Ingrese la cantidad de productos: ")

    product = {'name': name, 'price': price, 'amount': amount}
    inventary.append(product)
    print(f"El producto '{name}' fue añadido.")

# Función para consultar un producto por nombre
def consult_product(name):
    for i in inventary:
        if i['name'] == name:
            return i
    return None

# Función para actualizar el precio de un producto
def update_price():
    name = input("Nombre del producto a actualizar: ").strip().lower()
    product = consult_product(name)
    if product:
        new_price = number_invalid("Nuevo precio: $")
        product['price'] = new_price
        print("Precio actualizado.")
    else:
        print("Producto no encontrado.")

# Función para eliminar un producto del inventario
def delete_product():
    name = input("Nombre del producto a eliminar: ").strip().lower()
    producto = consult_product(name)
    if producto:
        inventary.remove(producto)
        print(f"El producto '{name}' fue eliminado del inventario.")
    else:
        print("Producto no encontrado en el inventario.")

# Función lambda para calcular el valor total del inventario
calculate_total_value = lambda: sum(p['price'] * p['amount'] for p in inventary)

# Función para mostrar los productos
def see_product():
    if not inventary:
        print("El inventario está vacío.")
    else:
        print("\nProductos en inventario:")
        print("{:<20} {:>10} {:>10}".format("Nombre", "Precio", "Cantidad"))
        print("-" * 42)
        for i in inventary:
            nombre = i["name"]
            precio = f"${i['price']:.2f}"
            cantidad = f"{int(i['amount'])}" if i["amount"].is_integer() else f"{i['amount']}"
            print("{:<20} {:>10} {:>10}".format(nombre, precio, cantidad))

# Bucle principal del programa
def menu():
    while True:
        print("""
Bienvenido al inventario
1. Añadir producto al inventario
2. Consultar producto en el inventario
3. Actualizar precio del producto
4. Eliminar producto del inventario
5. Valor total del inventario
6. Mostrar productos en inventario
7. Salir
-----------------------------------------------""")
        option = input("Seleccione el número del requerimiento que desea utilizar: ").strip()
        
        if option == "1":
            enter_product()
        elif option == "2":
            nombre = input("Nombre del producto a buscar: ").strip().lower()
            producto = consult_product(nombre)
            if producto:
                print(f"Producto: {producto['name']}, Precio: ${producto['price']:.2f}, Cantidad: {producto['amount']}")
            else:
                print("Producto no encontrado.")
        elif option == "3":
            update_price()
        elif option == "4":
            delete_product()
        elif option == "5":
            total = calculate_total_value()
            print(f"Valor total del inventario: ${total:.2f}")
        elif option == "6":
            see_product()
        elif option == "7":
            print("Saliendo del programa.")
            break
        else:
            print("Opción no válida. Intente nuevamente.")

# Punto de entrada del programa
if __name__ == "__main__":
    menu()




