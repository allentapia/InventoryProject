# InventoryProject
Inventory code 
package JoyerosTapia;

	import java.util.ArrayList;
	import java.util.List;
	import java.util.stream.Collectors;

	public class Inventario {
	    public static void main(String[] args) {
	        Joyeria joyeria = new Joyeria();
	        joyeria.agregarJoya("Anillo", "Oro", 10, 500);
	        Reloj reloj = new Reloj("Rolex", "Submariner", "123456", 8000, 12000, "2021-01-01");
	        joyeria.agregarReloj(reloj);
	        joyeria.mostrarInventario();
	    }
	}

	class Reloj {
	    private String marca;
	    private String modelo;
	    private String numero_serie;
	    private double costo;
	    private double precio_venta;
	    private String fecha_compra;
	    private String fecha_venta;
	    private List<String> reparaciones;

	    public Reloj(String marca, String modelo, String numero_serie, double costo, double precio_venta, String fecha_compra, String fecha_venta, List<String> reparaciones) {
	        this.marca = marca;
	        this.modelo = modelo;
	        this.numero_serie = numero_serie;
	        this.costo = costo;
	        this.precio_venta = precio_venta;
	        this.fecha_compra = fecha_compra;
	        this.fecha_venta = fecha_venta != null ? fecha_venta : "No vendido";
	        this.reparaciones = reparaciones != null ? reparaciones : new ArrayList<>();
	    }

	    public Reloj(String marca, String modelo, String numero_serie, double costo, double precio_venta, String fecha_compra) {
	        this(marca, modelo, numero_serie, costo, precio_venta, fecha_compra, null, new ArrayList<>());
	    }

	    @Override
	    public String toString() {
	        String reparacionesStr = reparaciones.isEmpty() ? "Ninguna" : String.join(", ", reparaciones);
	        return "Marca: " + marca + ", Modelo: " + modelo + ", Número de Serie: " + numero_serie +
	                ", Costo: " + costo + ", Precio de Venta: " + precio_venta + ", Fecha de Compra: " + fecha_compra +
	                ", Fecha de Venta: " + fecha_venta + ", Reparaciones: " + reparacionesStr;
	    }
	}

	class Joyeria {
	    private List<Reloj> inventario_relojes;
	    private List<Joya> inventario_joyas;

	    public Joyeria() {
	        inventario_joyas = new ArrayList<>();
	        inventario_relojes = new ArrayList<>();
	    }

	    public void agregarJoya(String tipo, String material, int cantidad, double precio) {
	        Joya joya = new Joya(tipo, material, cantidad, precio);
	        inventario_joyas.add(joya);
	    }

	    public void agregarReloj(Reloj reloj) {
	        inventario_relojes.add(reloj);
	    }

	    public void mostrarInventario() {
	        System.out.println("Inventario de Joyas:");
	        for (Joya joya : inventario_joyas) {
	            System.out.println(joya);
	        }

	        System.out.println("\nInventario de Relojes:");
	        for (Reloj reloj : inventario_relojes) {
	            System.out.println(reloj);
	        }
	    }
	}

	class Joya {
	    private String tipo;
	    private String material;
	    private int cantidad;
	    private double precio;

	    public Joya(String tipo, String material, int cantidad, double precio) {
	        this.tipo = tipo;
	        this.material = material;
	        this.cantidad = cantidad;
	        this.precio = precio;
	    }

	    @Override
	    public String toString() {
	        return "Tipo: " + tipo + ", Material: " + material + ", Cantidad: " + cantidad + ", Precio: " + precio;
	    }



	
	}

