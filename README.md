Biblioteca.cpp
==============
//Programa para biblioteca

/* Cristhian Rosillo
** UPIICSA@upiicsalibre
** twitter @Raker121
** 03.10.2012
*/
#include<stdio.h>
#include<stdlib.h>
#include<string.h>

struct Libro{
    int activo; //1= activo 0=prestado
    int registro;
    char titulo[50];
    char autor[40];
    char editorial[30];
    int numPaginas;
    int anoEdicion;
    char genero[15];
    char prestamo[50];
}biblio[100],btemporal;

int total;

int main(){
//Variables temporales y submenus
    char titulo[50];
    char autor[40];
    char editorial[30];
    int numPaginas;
    int anoEdicion;
    char genero[15];
    int i, op,op2,op3,op4,reg;
    char prestamo[50];

//Registros pre-establecidos

    biblio[0].activo=1;
  biblio[0].registro=0;
    strcpy(biblio[0].titulo,"Tu tiempo");
    strcpy(biblio[0].autor,"Victor Hernandez Ramirez");
    strcpy(biblio[0].editorial,"Libro para Todos");
    biblio[0].numPaginas=182;
    biblio[0].anoEdicion=2006;
    strcpy(biblio[0].genero,"Personal");

    biblio[1].activo=1;
	biblio[1].registro=1;
    strcpy(biblio[1].titulo,"Ovnis, SOS a la Humanidad");
    strcpy(biblio[1].autor,"J.J. Benitez");
    strcpy(biblio[1].editorial,"Alguno");
    biblio[1].numPaginas=49;
    biblio[1].anoEdicion=1984;
    strcpy(biblio[1].genero,"Reportaje");

    biblio[2].activo=1;
	biblio[2].registro=2;
    strcpy(biblio[2].titulo,"Cuentos para niños");
    strcpy(biblio[2].autor,"Alfonso Quiroga");
    strcpy(biblio[2].editorial,"Fondo de Cultura Economica");
    biblio[2].numPaginas=254;
    biblio[2].anoEdicion=2003;
    strcpy(biblio[2].genero,"Infantil");

	biblio[3].activo=1;
	biblio[3].registro=3;
    strcpy(biblio[3].titulo,"Historia Universal");
    strcpy(biblio[3].autor,"Francisco Gonzalez");
    strcpy(biblio[3].editorial,"Grant Hill");
    biblio[3].numPaginas=233;
    biblio[3].anoEdicion=2008;
    strcpy(biblio[3].genero,"Historia");

    total=3; //0 y 1

//Presentacion
 printf("\n\n\n\n\n\n\n\n\n\t\t\t   ************************");
    printf("\n\t\t\t   *Servicio Bibliotecario*");
    printf("\n\t\t\t   ************************\n\n\n\n\n\n\n\n\n\n\n\n\n");
    system("pause");

//Menú
    do{
          system("cls");
          printf("                MENU\n\n");
          printf("Seleccione opcion deseada y presione enter\n\n");
          printf("\t1.- Alta de libro\n");
          printf("\t2.- Baja de libro\n");
          printf("\t3.- Cambiar datos de libro\n");
          printf("\t4.- Mostrar Libros\n");
          printf("\t5.- Exportar a archivo\n");
          printf("\t6.- Prestamo\n");
          printf("\t7.- Devolucion\n");
          printf("\t8.- Salir\n");
          printf("\n\n           Opcion: ");
          scanf("%d",&op);
          system("cls");
//Agregar registros
          if(op==1){
              printf("1.- Alta\n");
              printf("Introduce el titulo: ");
              scanf("%s",&titulo);
              fflush(stdin);
              printf("Introduce el autor: ");
              scanf("%s",&autor);
              fflush(stdin);
              printf("Introduce la editorial: ");
              scanf("%s",&editorial);
              fflush(stdin);
              printf("Introduce el número de paginas: ");
              scanf("%d",&numPaginas);
              fflush(stdin);
              printf("Introduce el genero: ");
              scanf("%s",&genero);
              fflush(stdin);
              printf("Introduce el año de publicación: ");
              scanf("%d",&anoEdicion);
              fflush(stdin);

              total++;//Incrementa total
              biblio[total].activo=1;

              //Copa de temporales a Estructura
			  biblio[total].registro=total;
              strcpy(biblio[total].titulo, titulo);
              strcpy(biblio[total].autor, autor);
              strcpy( biblio[total].editorial, editorial);
              biblio[total].numPaginas=numPaginas;
              biblio[total].anoEdicion=anoEdicion;
              strcpy(biblio[total].genero,genero);

              printf("\n\n\nSe agrego el registro %d\n", total+1);

              system("pause");
          }
//Eliminar Registros
          if (op==2){
              printf("2.- Baja\n");
              printf("Elemento a eliminar");
              scanf("%d",& reg);
              reg--;
              for (i=reg;i<total;i++){// Recorre los registros
                    btemporal=biblio[i+1];
                    biblio[i]=btemporal;
              }
			  total--;
              system("pause");
            }
//Cambiar Registros
          if(op==3){
              printf("3.- Cambiar\n");
              printf("Registro a cambiar: ");
              scanf("%d",&reg);
                reg--;
                //Muestra Datos de registro seleccionado
              printf("\n   Datos actuales: \n\n");
              printf("         Registro: %d\n", biblio[reg].registro+1);
              printf("           Titulo: %s\n", biblio[reg].titulo);
              printf("            Autor: %s\n", biblio[reg].autor);
              printf("        Editorial: %s\n", biblio[reg].editorial);
              printf("Numero de Paginas: %d\n", biblio[reg].numPaginas);
              printf("           Genero: %s\n", biblio[reg].genero);
              printf("   Año de edición: %d\n\n", biblio[reg].anoEdicion);
              printf("Que elemento deseas cambiar?\n");
            //Menu para cambio en registros
              printf(" 1. Titulo\n 2. Autor\n 3. Editorial\n 4. Numero de Paginas\n 5. Genero\n 6. Año de edicion\n");
              scanf("%d",&op2);
                    if(op2==1){//Cambiar Titulo
                        printf("1. Cambiar Titulo\n");
                        printf("Introduce el titulo: ");
                        scanf("%s",&titulo);
                        fflush(stdin);
                        strcpy(biblio[reg].titulo, titulo);
                        system("cls");
                        printf("\nTitulo cambiado.\n");
                        system("pause");
                    }
                    if(op2==2){//Cambiar Autor
                        printf("2. Cambiar Autor\n");
                        printf("Introduce el autor: ");
                        scanf("%s",&autor);
                        fflush(stdin);
                        strcpy(biblio[reg].autor, autor);
                        system("cls");
                        printf("\nAutor cambiado.\n");
                        system("pause");
                    }
                    if(op2==3){//Cambiar Editorial
                        printf("3. Cambiar Editorial\n");
                        printf("Introduce el editorial: ");
                        scanf("%s",&editorial);
                        fflush(stdin);
                        strcpy(biblio[reg].editorial, editorial);
                        system("cls");
                        printf("\nEditorial cambiado.\n");
                        system("pause");
                    }
                    if(op2==4){//Cambiar # de paginas
                        printf("4. Cambiar Numero de Paginas\n");
                        printf("Introduce el Numero de Paginas: ");
                        scanf("%d",&numPaginas);
                        fflush(stdin);
                        biblio[reg].numPaginas=numPaginas;
                        system("cls");
                        printf("\nNumero de Paginas cambiado.\n");
                        system("pause");
                    }
                    if(op2==5){//Cambiar Genero
                        printf("5. Cambiar Genero\n");
                        printf("Introduce el Genero: ");
                        scanf("%s",&genero);
                        system("cls");
                        fflush(stdin);
                        strcpy(biblio[reg].genero, genero);
                    }
                    if(op2==6){//Cambiar Año de Edicion
                        printf("6. Cambiar Año de Edicion\n");
                        printf("Introduce el año de edicion: ");
                        scanf("%d",&anoEdicion);
                        fflush(stdin);
                        biblio[reg].anoEdicion=anoEdicion;
                        system("cls");
                        printf("\nAño de Edicion cambiado.\n");
                        system("pause");
                    }
          }
//Muestra todos los registros disponibles
          if(op==4){
              printf("3.- Mostrar\n\n");
              printf("1. Todos los Libros\n2. Libros Disponibles\n3. Libros Prestados\n ");//Menu
              scanf("%d",&op3);
              system("cls");

              if(op3==1){//Muesta Todos los registros
                  for(i=0;i<=total;i++){
                      printf("         Registro: %d\n", biblio[i].registro+1);
                      printf("           Titulo: %s\n", biblio[i].titulo);
                      printf("            Autor: %s\n", biblio[i].autor);
                      printf("        Editorial: %s\n", biblio[i].editorial);
                      printf("Numero de Paginas: %d\n", biblio[i].numPaginas);
                      printf("           Genero: %s\n", biblio[i].genero);
                      printf("   Año de edición: %d\n\n", biblio[i].anoEdicion);
                  }
              }
              if(op3==2){//Muesta Registros Activos (Libros disponibles)
                  printf("Libros Disponibles\n\n");
                  for(i=0;i<=total;i++){
                    if (biblio[i].activo==1){
                      printf("         Registro: %d\n", biblio[i].registro+1);
                      printf("           Titulo: %s\n", biblio[i].titulo);
                      printf("            Autor: %s\n", biblio[i].autor);
                      printf("        Editorial: %s\n", biblio[i].editorial);
                      printf("Numero de Paginas: %d\n", biblio[i].numPaginas);
                      printf("           Genero: %s\n", biblio[i].genero);
                      printf("   Año de edición: %d\n\n", biblio[i].anoEdicion);
                    }
                  }
              }
              if(op3==3){//Muesta Registros Inactivos = 0 (Libros Prestados)
                  for(i=0;i<=total;i++){
                    if (biblio[i].activo==0){
                      printf("         Registro: %d\n", biblio[i].registro+1);
                      printf("           Titulo: %s\n", biblio[i].titulo);
                      printf("            Autor: %s\n", biblio[i].autor);
                      printf("        Editorial: %s\n", biblio[i].editorial);
                      printf("Numero de Paginas: %d\n", biblio[i].numPaginas);
                      printf("           Genero: %s\n", biblio[i].genero);
                      printf("   Año de edición: %d\n\n", biblio[i].anoEdicion);
                      printf("       Prestado A: %s\n\n", biblio[i].prestamo);
                    }
                  }
              }
              system ("pause");
          }
//Creacion de archivos
          if(op==5){
              printf("5.- Creacion de un archivo\n\n");
              printf("1. Archivo de un libro\n2. Libros Disponibles\n3. Libros Prestados\n4. Todos los Libros\nArchivo a crear: ");//Menu
              scanf("%d",&op4);

              if(op4==1){//Archivo de un libro
                  printf("Registro del Libro para crear archivo: ");
                  scanf("%d",&reg);
                   reg--;

              FILE *arc;
              arc=fopen("Libro.txt","w");

              strcpy(titulo,biblio[reg].titulo);
              strcpy(editorial,biblio[reg].editorial);
              strcpy(genero,biblio[reg].genero);
              strcpy(autor,biblio[reg].autor);

              fprintf(arc,"           Titulo: %s\n",titulo);
              fprintf(arc,"            Autor: %s\n",autor);
              fprintf(arc,"        Editorial: %s\n",editorial);
              fprintf(arc,"           Genero: %s\n",genero);
              fclose(arc);
              system("cls");
              printf("Archivo creado\n\n\n\n");
              system("pause");
              }
            if(op4==2){//Archivo Libros Disponibles

              FILE *arc;
              arc=fopen("Libros Disponibles.txt","a");

              for(i=0;i<=total;i++){
                    if (biblio[i].activo==1){
              strcpy(titulo,biblio[i].titulo);
              strcpy(editorial,biblio[i].editorial);
              strcpy(genero,biblio[i].genero);
              strcpy(autor,biblio[i].autor);

              fprintf(arc,"           Titulo: %s\n",titulo);
              fprintf(arc,"            Autor: %s\n",autor);
              fprintf(arc,"        Editorial: %s\n",editorial);
              fprintf(arc,"           Genero: %s\n\n",genero);

                    }
                }
              fclose(arc);
              system("cls");
              printf("Archivo creado\n\n\n\n");
              system("pause");
                          }
            if(op4==3){//Archivo Libros Prestados

              FILE *arc;
              arc=fopen("Libro Prestados.txt","a+");

              for(i=0;i<=total;i++){
                    if (biblio[i].activo==0){
              strcpy(titulo,biblio[i].titulo);
              strcpy(editorial,biblio[i].editorial);
              strcpy(genero,biblio[i].genero);
              strcpy(autor,biblio[i].autor);
              strcpy(prestamo,biblio[i].prestamo);

              fprintf(arc,"           Titulo: %s\n",titulo);
              fprintf(arc,"            Autor: %s\n",autor);
              fprintf(arc,"        Editorial: %s\n",editorial);
              fprintf(arc,"           Genero: %s\n",genero);
              fprintf(arc,"       Prestado a: %s\n\n",prestamo);

                    }
                }
                    fclose(arc);
              system("cls");
              printf("Archivo creado\n\n\n\n");
              system("pause");

            }
              if(op4==4){//Todos Libros Archivo

              FILE *arc;
              arc=fopen("Libros.txt","a");

              for(i=0;i<=total;i++){
              strcpy(titulo,biblio[i].titulo);
              strcpy(editorial,biblio[i].editorial);
              strcpy(genero,biblio[i].genero);
              strcpy(autor,biblio[i].autor);

              fprintf(arc," Titulo: %s\n",titulo);
              fprintf(arc,"            Autor: %s\n",autor);
              fprintf(arc,"        Editorial: %s\n",editorial);
              fprintf(arc,"           Genero: %s\n\n",genero);

                    }

                    fclose(arc);
              system("cls");
              printf("Archivo creado\n\n\n\n");
              system("pause");
              }
    }
//Prestamo de Libros
          if(op==6){
              printf("3.- Prestamo\n");
              printf("Seleccione el Numero de registro del libro a Prestar: ");
              scanf("%d",& reg);
              reg--;

              if(biblio[reg].activo==1){//Verificar si el libro esta disponible
              printf("\n   Datos del libro: \n\n");
              printf("         Registro: %d\n", biblio[reg].registro+1);
              printf("           Titulo: %s\n", biblio[reg].titulo);
              printf("            Autor: %s\n", biblio[reg].autor);
              printf("        Editorial: %s\n", biblio[reg].editorial);
              printf("Numero de Paginas: %d\n", biblio[reg].numPaginas);
              printf("           Genero: %s\n", biblio[reg].genero);
              printf("   Año de edición: %d\n\n", biblio[reg].anoEdicion);
              printf("A quien prestara el libro?\n");

              scanf("%s",&prestamo);
              fflush(stdin);
              strcpy(biblio[reg].prestamo,prestamo);
              biblio[reg].activo=0; //cambio a "inactivo"

              system("cls");
              printf("Libro prestado a: %s\n\n\n\n\n",prestamo);
              system("pause");

              }
              else{//Libro ya prestado
                  system("cls");
                  strcpy(prestamo,biblio[reg].prestamo);
                  printf("Este libro ya ah sido prestado a : %s\n\n\n\n\n",prestamo);
                  system("pause");
              }
          }
//Devolucion
          if(op==7){
              printf("3.- Devolucion\n");
              printf("Seleccione el Numero de registro del libro a Devolver: ");
              scanf("%d",& reg);
              reg--;
              printf("\n   Datos del libro: \n\n");
              printf("         Registro: %d\n", biblio[reg].registro+1);
              printf("           Titulo: %s\n", biblio[reg].titulo);
              printf("            Autor: %s\n", biblio[reg].autor);
              printf("        Editorial: %s\n", biblio[reg].editorial);
              printf("Numero de Paginas: %d\n", biblio[reg].numPaginas);
              printf("           Genero: %s\n", biblio[reg].genero);
              printf("   Año de edición: %d\n\n", biblio[reg].anoEdicion);
              printf("Libro devuelto\n\n");
              system("pause");

              biblio[reg].activo=1; //cambio a "activo"
          }
    }
//Salir
    while(op<8);
    printf("Adios...\n");
    getchar();
    return 0;
}
