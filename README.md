# Proyecto
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
			double R,V,T,RC,C,Q,A,euler=2.718281828;
			//Aqui quiero que salgan un espacio en blanco donde se pueda clickear y colocar el valor en cada uno
			System.out.println("Ingrese el voltaje de la fuente "+   "(Voltios).");V=S.nextInt();
			System.out.println("Ingrese el valor de la resistencia "+  "(Ohm).");R=S.nextInt();
			System.out.println("Ingrese el valor del condensador "+  "(MicroFaradios).");C=S.nextInt();
			C=C*Math.pow(10,-6);
			
			A=V/R;
			System.out.println("La intensidad maxima del circuito es: "+A+"(Ampherios)");
			
			Q=C*V;
			System.out.println("La Carga maxima del condensador sera: "+Q+"(Coulomb)");
			
			RC=R*C;

			//Aqui quiero que el usuario escoja el tiempo que se carga el condensador
			System.out.println("Ingrese a cuantos segundos se carga el condensador: ");
			T=S.nextInt();
			
			A=(V/R)*Math.pow(euler,-T/RC);
			System.out.println("La intensidad es de: "+A+"(Ampherios).");
			
			Q=C*V*(1-Math.pow(euler,-T/RC));
			System.out.println("El condensador tendra una carga de: "+Q+"(Coulomb).");
		}
		//Si escoje descarga de condensadores
		if(opcion==2){
			double R,Vi,T,RC,C,V,Q,A,euler=2.718281828;
			//Aqui quiero que salgan un espacio en blanco donde se pueda clickear y colocar el valor en cada uno
			System.out.println("Ingrese el voltaje inicial "+   "(Voltios).");Vi=S.nextInt();
			System.out.println("Ingrese el valor de la resistencia "+  "(Ohm).");R=S.nextInt();
			System.out.println("Ingrese el valor del condensador "+  "(MicroFaradios).");C=S.nextInt();
			C=C*Math.pow(10,-6);
			
			A=Vi/R;
			System.out.println("La intensidad maxima del circuito es: "+A+"(Ampherios)");
			
			Q=C*Vi;
			System.out.println("La Carga tiene un valor maximo inicial de: "+Q+"(Coulomb)");
			
			RC=R*C;
			//Aqui quiero que el usuario escoja el tiempo que se descarga el condensador
			System.out.println("Ingrese la cantidad de segundos que se descarga el condensador: ");
			T=S.nextInt();
			
			V=Vi*Math.pow(euler,-T/RC);
			System.out.println("El condensador tendra un voltaje de: "+V+"(Voltios).");
			
			Q=C*V*(1-Math.pow(euler,-T/RC));
			System.out.println("El condensador tendra una carga de: "+Q+"(Coulomb).");
			
			A=(V/R)*Math.pow(euler,-T/RC);
			System.out.println("La intensidad es de: "+A+"(Ampherios).");
		}
	}
}
