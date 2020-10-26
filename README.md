# Proyecto-

#include <iostream>
#include <string>
#pragma once

using namespace std;

class Actor
{
public:
    Actor();
    Actor(int id, string nombre);
    int getID(){return id;};
    void setID(int i){id=i;};
    string getNombre(){return nombre;};
    void setNombre(string nom){nombre=nom;};
    void muestra();
protected:
    int id;
    string nombre;
};

Actor::Actor()
{
    id = 1;
    nombre = "Manuel";
}

Actor::Actor(int i, string nom)
{
    id = i;
    nombre = nom;
}

void Actor::muestra()
{
    cout<<"ID: "<<id<<"  Nombre: "<<nombre<<endl;
}


//Clase Película  set es igualar a la variable y get es el return
class Pelicula
{
public:

    Pelicula();
    void setNumPeli(int num){numPeli=num;};
    int getNumPeli(){return numPeli;};
    void setTitulo(string t){titulo=t;};
    string getTitulo(){return titulo;};
    void setAnio(int a){anio=a;};
    int getAnio(){return anio;};
    void setDuracion(int d){duracion=d;};
    int getDuracion(){return duracion;};
    void setGenero(string g){genero=g;};
    string getGenero(){return genero;};
    int getCantActores(){return cantActores;};


protected:
    Actor listaActores[10];
    int numPeli, anio, duracion, cantActores;
    string titulo, genero;
};

Pelicula::Pelicula()
{
    numPeli = 1;
    anio = 2000;
    duracion = 120;
    titulo = "Megalodon";
    genero = "Suspenso";
//    listaActores = [];
}


//Clase Hora
class Hora
{
public:
    Hora();
    Hora(int hh, int mm);
    int getHora(){return hh;};
    void setHora(int h){hh=h;};
    int getMin(){return mm;};
    void setMin(int m){mm=m;};
    void muestra();
protected:
    int hh, mm;
};

Hora::Hora()
{
    hh = 10;
    mm = 30;
}

Hora::Hora(int h, int m)
{
    hh = h;
    mm = m;
}

void Hora::muestra()
{
    cout<<"Hora: "<<hh<<"  con "<<mm<<"  minutos"<<endl;
}


//Clase Función
class Funcion
{
public:
    Funcion();
    Funcion(Hora h, string cve, int nump, int s);
    string getCVEFuncion(){return cveFuncion;};
    void setCVEFuncion(string cve){cveFuncion=cve;};
    int getNumpeli(){return numPeli;};
    void setNumpeli(int nump){numPeli=nump;};
    int getSala(){return sala;};
    void setSala(int s){sala=s;};
    Hora gethora();
    void sethora(Hora h);
    void muestra();

protected:
    string cveFuncion;
    int numPeli, sala;
    Hora hora;
};

Funcion::Funcion()
{
    Hora h1;
    cveFuncion = "A113";
    numPeli = 1;
    sala = 1;
    hora = h1;

}

Funcion::Funcion(Hora h, string cve, int nump, int s)
{
    cveFuncion = cve;
    numPeli = nump;
    sala = s;
    hora = h;
}

Hora Funcion::gethora()
{
    return hora;
}

void Funcion::sethora(Hora h)
{
    hora = h;
}

void Funcion::muestra()
{
    cout<<"Clave de la funcion: "<<cveFuncion<<"  Numero de pelicula: "<<numPeli<<"  Sala: "<<sala<<endl;
}

//MAIN

#include <iostream>
#include "Proyecto.h"
#include <fstream>
#include <string>
#pragma once

using namespace std;

int main()
{

    Actor actor[20];
    Funcion funcion[20];
    Pelicula pelicula[20];

    ifstream archE;

    //Lista de actores
    archE.open("actores.txt");
    int i;
    string linea;
    string nom;
    int cont = 0;

    getline(archE, linea);

    while (archE >> i >> nom)
    {
        actor[cont].setID(i);
        actor[cont].setNombre(nom);
        cont++;
    }
    archE.close();


        ifstream archE2;

    //Lista de peliculas
    archE2.open("peliculas.txt");
    int num;
    string t;
    int a;
    int d;
    string g;
    int conta = 0;

    getline(archE2, linea);

    while (archE >> num >> a >> d >> g)
    {
        pelicula[conta].setNumPeli(num);
        pelicula[conta].setTitulo(t);
        pelicula[conta].setAnio(a);
        pelicula[conta].setDuracion(d);
        pelicula[conta].setGenero(g);
        cont++;
    }
    archE2.close();

    //Menu
    char opcion;
    while (opcion != 'f')
    {
        cout << "\na. Mostrar actores" << endl;
        cout << "b. Mostrar peliculas" << endl;
        cout << "c. Funciones disponibles" << endl;
        cout << "d. Funciones por hora" << endl;
        cout << "e. Consulta por clave de funcion" << endl;
        cout << "f. Pelicula por actor" << endl;
        cout << "g. Terminar" << endl;
        cout << "\nIngrese la opcion que quiera ver: "; cin >> opcion;
    }
    return 0;
}
