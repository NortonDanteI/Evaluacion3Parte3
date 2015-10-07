# Proyecto
//De Aqui empieza el código.
import java.util.Scanner;
public class ProyectoFisica {
	public static void main(String[] arg){
		
		System.out.println("Proyecto de física ");
		System.out.println("Carga y descarga de condensadores");
		int opcion;
		Scanner S = new Scanner(System.in); 
		//Quiero aqui en realidad tener un boton que deje escojer entre carga y descarga, y no estos printf
		System.out.println("Escoje 1 para carga de condensadores.");
		System.out.println("Escoje 2 para descarga de condensadores.");
		opcion=S.nextInt();
		//Si el usuario escoje carga de condensadores
		if(opcion==1){
			//Aqui quiero que salgan un espacio en blanco donde se pueda clickear y colocar el valor en cada uno
			System.out.println("Ingrese el voltaje de la fuente.(V)");
			System.out.println("Ingrese el valor de la resistencia.(Ohm)");
			System.out.println("Ingrese el valor del condensador (microfaradios).");
			
			
			
		}
	}
}
