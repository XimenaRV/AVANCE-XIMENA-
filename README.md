//Ximena Gualupe Rosales Velazquez 08/09/22 2086234

```
#include<iostream>
#include<conio.h>
#include<string.h>
#include<string>

using namespace std;
struct nodo{
    float precio;
    string articulo, descripcion, categoria;
    int num_articulo;
    struct nodo *sgte;
};

void AgregarProducto(struct nodo *lista, int nart, string arti, string desc, string cate, int pre){
     nodo *q=new nodo();
	 nodo *t=new nodo();
    t=lista;
    q->num_articulo=nart;
    q->articulo=arti;
    q->descripcion=desc;
    q->categoria=cate;
    q->precio=pre;
    if(lista->sgte!=NULL){
        while(t->sgte!=NULL){
            t=t->sgte;
        }
        q->sgte=NULL;
        t->sgte=q;
    }else{
        q->sgte=NULL;
        lista->sgte=q;
    }
    
}

void MostrarLista(struct nodo *lista){
	nodo *p=new nodo();
	p=lista->sgte;
	if(lista->sgte!=NULL){
		while(p!=NULL){
			cout<<"\tN. Articulo: "<<p->num_articulo<<endl;
			cout<<"\tArticulo: "<<p->articulo<<endl;
			cout<<"\tCategoria: "<<p->categoria<<endl;
			cout<<"\tDescripcion: "<<p->descripcion<<endl;
			cout<<"\tPrecio: "<<p->precio<<endl;
			cout<<" "<<endl;
			p=p->sgte;
		}
	}else{
		cout<<"No hay productos."<<endl;
		cout<<" "<<endl;
	}
	
}

int main()
{
	nodo *ListaP=new nodo();
    ListaP->sgte=NULL;
   int opcion, n_art,resp=1;
   float price;
   string art, desc,cate;
do{
cout << "/t Tienda de videojuegos: PACMAN \n";//nombre de la tienda de videojuegos
cout <<" 1.-Agregar articulo\n 2.-Modificar articulo\n 3.-Eliminar articulo\n 4.-Lista de articulos\n 5.-Limpiar pantalla\n 6.-Salir\n";//opciones que deberían salir en el menu;
cin >>opcion ;

switch (opcion)
{
    case 1: //Agregar articulo
    cout <<"Ingrese el numero del articulo: \n";
    cin >>n_art;
    cout <<endl<<"Ingrese el nombre del articulo: \n";
    cin.ignore();
    getline(cin, art);
    cout<<endl<< "Ingrese la descripcion del articulo: \n";
    cin.ignore();
    getline(cin, desc);
    cout<<endl<<"Ingrese la categoria del articulo: \n";
    cin.ignore();
    getline(cin, cate);
    cout<<endl<<"Ingrese el precio base del articulo: \n";
    cin >>price;
    price*=1.16;
    cout<<" "<<endl;
    AgregarProducto(ListaP,n_art,art,desc,cate,price);
    break;
    case 2: //Modificar articulo
    cout<<"Por agregar funcion."<<endl;
    break;
    case 3: //Eliminar articulo
        cout<<"Por agregar funcion."<<endl;
    break;
    case 4:
    	MostrarLista(ListaP);
    break;
    case 5:
        system("cls");
    break;
    case 6: //Salir
    do{
	cout<<"\tDesea volver salir del programa?"<<endl;
	cout<<"1. No."<<endl;
	cout<<"0. Si, salir."<<endl;
	cin>>resp;
	}while(resp!=0&&resp!=1);
    if(resp==0){
	cout<< "Gracias por su compra\n";
	}	
    break;
    default:
    cout<<"Ingrese una opcion correcta\n"; //Por si se equivoca la persona, volver al menu principal
}

}while(resp!=0);
    
}
