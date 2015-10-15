# Evaluacion3Parte3
/*-------------------------------------Norton John Irarrázabal Callejas-----------------------------------------------------*/
/*-----------------------------------------------Tabla Hash-----------------------------------------------------------------*/
/*----------------------------------------------Bibliotecas-----------------------------------------------------------------*/
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>
#define indice 5404
#define tam 30
/*-------------------------------------------Definir estructuras-------------------------------------------------------------*/
typedef struct registro{
    int Clave,N_fax;
    char Fecha[tam],Nombre_producto[tam],Nombre_fabricante[tam],
		 Pais_origen[tam],Tipo_insumo[tam],Especie_destino[tam],Presentacion[tam];
}Registro;
/*-------------------------------------------------------------------------------------------------------------------------*/
typedef struct nodo{
    Registro datos;
    struct nodo *siguiente_dato;
}Nodo;
/*-----------------------------------------------------funciones-----------------------------------------------------------*/
void inicializar_tabla(Nodo *Tabla[indice]){
	for(int b=0;b<indice;b++){
    	Tabla[b]=NULL;
    }
}
/*-------------------------------------------------------------------------------------------------------------------------*/
Registro extraer_datos(FILE *archivo_csv){
	Registro Datos_nuev;
	fscanf(archivo_csv,"%i;%i;%[^;];%[^;];%[^;];%[^;];%[^;];%[^;];%[^\n]\n",
	&Datos_nuev.Clave,&Datos_nuev.N_fax,&Datos_nuev.Fecha,&Datos_nuev.Nombre_producto,&Datos_nuev.Nombre_fabricante,
	&Datos_nuev.Pais_origen,&Datos_nuev.Tipo_insumo,&Datos_nuev.Especie_destino,
	&Datos_nuev.Presentacion);
	return (Datos_nuev);
}
/*-------------------------------------------------------------------------------------------------------------------------*/
int hash(int Clave){
	return(Clave%indice);
}
/*-------------------------------------------------------------------------------------------------------------------------*/
void colocar_datos_en_tabla(Nodo *Tabla[indice],Registro datos_nuevos,int indic){
	if(Tabla[indic]==NULL){
		Tabla[indic]=(Nodo*)malloc(sizeof(Nodo));
		Tabla[indic]->datos=datos_nuevos;
		Tabla[indic]->siguiente_dato=NULL;	
	}
	else{
		Nodo *Aux_nodo=(Nodo*)malloc(sizeof(Nodo));
		Aux_nodo=Tabla[indic];
		Aux_nodo->datos=datos_nuevos;
		Tabla[indice]->siguiente_dato=Aux_nodo;
	}
}
/*-------------------------------------------------------------------------------------------------------------------------*/
 void Buscar_en_tabla(Nodo *Tabla[indice]){
	int numero,indic,encontro=0;
	printf("Ingrese el numero del alimento\n");
    scanf("%i", &numero);
	Nodo *Aux_nodo=(Nodo*)malloc(sizeof(Nodo));
    indic=hash(numero);
    printf("valor hash: %i\n",indic);
	Aux_nodo=Tabla[indic];
	clock_t start = clock();
    while((Aux_nodo!=NULL)&&(!encontro)){
        if(Aux_nodo->datos.Clave==numero){
            printf("Tiempo transcurrido de Busqueda: %f\n", ((double)clock() - start) / CLOCKS_PER_SEC);
            encontro=1;
        }
        if(encontro==0){
        	Aux_nodo=Aux_nodo->siguiente_dato;
		}
    }
	if(Aux_nodo!=NULL){
        printf("Se encontraron los datos.\n");
        printf("Numero del alimento: %i\n", Aux_nodo->datos.Clave);
        printf("Numero de fax : %i\n", Aux_nodo->datos.N_fax);
        printf("Fecha: %s\n", Aux_nodo->datos.Fecha);
        printf("Nombre del producto: %s\n", Aux_nodo->datos.Nombre_producto);
        printf("Nombre del fabricante: %s\n", Aux_nodo->datos.Nombre_fabricante);
        printf("Pais de origen: %s\n", Aux_nodo->datos.Pais_origen);
        printf("Tipo de insumo: %s\n", Aux_nodo->datos.Tipo_insumo);
        printf("Especie de destino: %s\n", Aux_nodo->datos.Especie_destino);
        printf("Presentacion: %s\n", Aux_nodo->datos.Presentacion);
    }else{
        printf("\nLos Datos no se encuentran en la Tabla Hash.\n");
	}	
 }
/*--------------------------------------------------funcion principal-------------------------------------------------------*/
int main(){
	Nodo *Tabla[indice];
	inicializar_tabla(Tabla);getchar();
	int indic,a;
	char caracteres[500];
	Registro datos_nuevos;
	FILE *archivo_csv=fopen("insumosALIMENTACION_ver_007.csv","r");
	fscanf(archivo_csv,"%[^\n]",&caracteres);
	clock_t start = clock();
	for(int a=1;a<=indice;a++){	
		datos_nuevos=extraer_datos(archivo_csv);
		indic=hash(datos_nuevos.Clave);
		colocar_datos_en_tabla(Tabla,datos_nuevos,indic);
	}
	printf("Tiempo transcurrido de creacion de tabla: %f\n", ((double)clock() - start) / CLOCKS_PER_SEC);
	fclose(archivo_csv);getchar();
	Buscar_en_tabla(Tabla);getchar();getchar();getchar();
	return (1);
}
/*--------------------------------------------------------------------------------------------------------------------------*/
