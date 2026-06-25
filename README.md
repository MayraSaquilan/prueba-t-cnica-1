# prueba-t-cnica-1
   static ArrayList<Cliente> clientes = new ArrayList<>();
    static Scanner sc = new Scanner(System.in);
    static int contadorId = 1;

    public static void main(String[] args) {

        int opcion;

        do {
            System.out.println("\n===== GESTIÓN DE CLIENTES =====");
            System.out.println("1. Agregar cliente");
            System.out.println("2. Listar clientes");
            System.out.println("3. Actualizar cliente");
            System.out.println("4. Eliminar cliente");
            System.out.println("5. Buscar por ciudad");
            System.out.println("0. Salir");
            System.out.print("Opción: ");

            opcion = Integer.parseInt(sc.nextLine());

            switch (opcion) {
                case 1:
                    agregarCliente();
                    break;
                case 2:
                    listarClientes();
                    break;
                case 3:
                    actualizarCliente();
                    break;
                case 4:
                    eliminarCliente();
                    break;
                case 5:
                    buscarPorCiudad();
                    break;
                case 0:
                    System.out.println("Programa finalizado.");
                    break;
                default:
                    System.out.println("Opción incorrecta.");
            }

        } while (opcion != 0);
    }

    public static void agregarCliente() {

        System.out.print("Nombre: ");
        String nombre = sc.nextLine();

        while (nombre.isEmpty()) {
            System.out.print("El nombre es obligatorio: ");
            nombre = sc.nextLine();
        }

        System.out.print("Apellidos: ");
        String apellidos = sc.nextLine();

        System.out.print("Sexo: ");
        String sexo = sc.nextLine();

        System.out.print("Ciudad: ");
        String ciudad = sc.nextLine();

        System.out.print("Fecha nacimiento: ");
        String fecha = sc.nextLine();

        System.out.print("Teléfono: ");
        String telefono = sc.nextLine();

        System.out.print("Correo: ");
        String correo = sc.nextLine();

        Cliente cliente = new Cliente(
                contadorId++,
                nombre,
                apellidos,
                sexo,
                ciudad,
                fecha,
                telefono,
                correo
        );

        clientes.add(cliente);

        System.out.println("Cliente agregado correctamente.");
    }

    public static void listarClientes() {

        if (clientes.isEmpty()) {
            System.out.println("No hay clientes registrados.");
            return;
        }

        for (Cliente cliente : clientes) {
            System.out.println(cliente);
        }
    }

    public static void actualizarCliente() {

        System.out.print("Ingrese ID del cliente: ");
        int id = Integer.parseInt(sc.nextLine());

        for (Cliente cliente : clientes) {

            if (cliente.getId() == id) {

                System.out.print("Nuevo nombre: ");
                cliente.setNombre(sc.nextLine());

                System.out.print("Nuevos apellidos: ");
                cliente.setApellidos(sc.nextLine());

                System.out.print("Nuevo sexo: ");
                cliente.setSexo(sc.nextLine());

                System.out.print("Nueva ciudad: ");
                cliente.setCiudad(sc.nextLine());

                System.out.print("Nueva fecha nacimiento: ");
                cliente.setFechaNacimiento(sc.nextLine());

                System.out.print("Nuevo teléfono: ");
                cliente.setTelefono(sc.nextLine());

                System.out.print("Nuevo correo: ");
                cliente.setCorreo(sc.nextLine());

                System.out.println("Cliente actualizado.");
                return;
            }
        }

        System.out.println("Cliente no encontrado.");
    }

    public static void eliminarCliente() {

        System.out.print("Ingrese ID a eliminar: ");
        int id = Integer.parseInt(sc.nextLine());

        for (Cliente cliente : clientes) {

            if (cliente.getId() == id) {
                clientes.remove(cliente);
                System.out.println("Cliente eliminado.");
                return;
            }
        }

        System.out.println("Cliente no encontrado.");
    }

    public static void buscarPorCiudad() {

        System.out.print("Ciudad: ");
        String ciudad = sc.nextLine();

        boolean encontrado = false;

        for (Cliente cliente : clientes) {

            if (cliente.getCiudad().equalsIgnoreCase(ciudad)) {
                System.out.println(cliente);
                encontrado = true;
            }
        }

        if (!encontrado) {
            System.out.println("No existen clientes en esa ciudad.");
        }




public class Cliente{
private int id;
private String nombre;
private String apellidos;
private String sexo;
private String ciudad;
private String fechaNacimiento;
private String telefono;
private String correo;

private Cliente(int id, String nombre, String apellidos, String sexo,
                String ciudad, String fechaNacimiento,
                String telefono, String correo) {
    this.id = id;
    this.nombre = nombre;
    this.apellidos = apellidos;
    this.sexo = sexo;
    this.ciudad = ciudad;
    this.fechaNacimiento = fechaNacimiento;
    this.telefono = telefono;
    this.correo = correo;
}

    public static Cliente createCliente(int id, String nombre, String apellidos, String sexo,
                                        String ciudad, String fechaNacimiento,
                                        String telefono, String correo) {
        return new Cliente(id, nombre, apellidos, sexo, ciudad, fechaNacimiento, telefono, correo);
    }

    public int getId() {
    return id;
}

public String getCiudad() {
    return ciudad;
}

public void setNombre(String nombre) {
    this.nombre = nombre;
}

public void setApellidos(String apellidos) {
    this.apellidos = apellidos;
}

public void setSexo(String sexo) {
    this.sexo = sexo;
}

public void setCiudad(String ciudad) {
    this.ciudad = ciudad;
}

public void setFechaNacimiento(String fechaNacimiento) {
    this.fechaNacimiento = fechaNacimiento;
}

public void setTelefono(String telefono) {
    this.telefono = telefono;
}

public void setCorreo(String correo) {
    this.correo = correo;
}

@Override
public String toString() {
    return "ID: " + id +
            ", Nombre: " + nombre +
            ", Apellidos: " + apellidos +
            ", Sexo: " + sexo +
            ", Ciudad: " + ciudad +
            ", Fecha Nacimiento: " + fechaNacimiento +
            ", Teléfono: " + telefono +
            ", Correo: " + correo;
}
}
        
    }
}
