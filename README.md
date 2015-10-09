# Proyecto
import java.util.Scanner;
public class ProyectoFisica {
	public static void main(String[] arg){
		int opcion;
		Scanner S = new Scanner(System.in); 
		//Para carga de condensadores
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
			
		//Si escoje descarga de condensadores
		double Rpri,Vipri,Tpri,RpriCpri,Cpri,Vpri,Qpri,Apri,eulerpri=2.718281828;
		//Aqui quiero que salgan un espacio en blanco donde se pueda clickear y colocar el valor en cada uno
		System.out.println("Ingrese el voltaje inicial "+   "(Voltios).");Vipri=S.nextInt();
		System.out.println("Ingrese el valor de la resistencia "+  "(Ohm).");Rpri=S.nextInt();
		System.out.println("Ingrese el valor del condensador "+  "(MicroFaradios).");Cpri=S.nextInt();
		Cpri=Cpri*Math.pow(10,-6);
		
		Apri=Vipri/Rpri;
		System.out.println("La intensidad maxima del circuito es: "+A+"(Ampherios)");
		
		Qpri=Cpri*Vipri;
		System.out.println("La Carga tiene un valor maximo inicial de: "+Q+"(Coulomb)");
		
		RpriCpri=Rpri*Cpri;
		//Aqui quiero que el usuario escoja el tiempo que se descarga el condensador
		System.out.println("Ingrese la cantidad de segundos que se descarga el condensador: ");
		Tpri=S.nextInt();
			
		Vpri=Vipri*Math.pow(eulerpri,-Tpri/RpriCpri);
		System.out.println("El condensador tendra un voltaje de: "+Vpri+"(Voltios).");
			
		Qpri=Cpri*Vpri*(1-Math.pow(euler,-T/RpriCpri));
		System.out.println("El condensador tendra una carga de: "+Qpri+"(Coulomb).");
			
		Apri=(Vpri/Rpri)*Math.pow(euler,-Tpri/RpriCpri);
		System.out.println("La intensidad es de: "+Apri+"(Ampherios).");
	}
}
