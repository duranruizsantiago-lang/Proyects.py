print("----Wellcome to ATM cashup.----")

saldo = 1000
importe_minimo = 20
while True:
    print(f"\n====================")
    print(f"\nSALDO DE LA CUENTA: ${saldo}.")
    print(f"\n====================")
    print("1. Ingresar dinero.")
    print("2. Retirar dinero")
    print("3. Salir")   

    opcion = input("Seleccione opcion:")        

    

    if opcion == "1":
        try:
            ingreso = int(input("¿Cuanto desea ingresar: "))
            if ingreso > 0:
                 saldo += ingreso
                 print(f"Ingreso exitoso, has ingresado: ${ingreso}")
            else:                   
                 print("Error: el monto debe ser mayor a 0.")
        except ValueError:
            print("Error, ingrese un numero valido")

    elif opcion == "2":
        try:
            retiro = int(input(f"¿Cuanto desea retirar (minimo ${importe_minimo}):"))
            
            if retiro < importe_minimo:
                print(f"Error: el importe minimo a retirar es: ${importe_minimo}.")
            
            elif retiro > saldo:
                print("Error: fondos insuficientes.")

            else:
                saldo -= retiro
                print(f"Retiro realizado. retire su dinero, su nuevo saldo es: ${saldo} ")

        except ValueError:
             print("Digite solo numeros validos (numeros enteros")

    elif opcion == "3" or opcion.lower() == "salir":
        print("Gracias por usar ATM cashup. ¡HASTA PRONTRO!.")
        break
    
    else:
        print("opcion no valida, intente de nuevo.")
         

                               

   
