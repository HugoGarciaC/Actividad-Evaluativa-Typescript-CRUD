# Actividad-Evaluativa-Typescript-CRUD

/*Actividad Evaluativa: Typescript:
La siguiente actividad permitira observar los conocimeintos adquiridos sobre typescript:
- Tipos de datos
- Tipado fuerte
- Herencia
- Interfaz
tendra un 50% del valor de la nota de esta semana:

Estructura: Utiliza el siguiente diseño para realizar el CRUD correspondiente:*/

class Mascotas {
    Id: number = 0;
    Nombre: string = "";
    Especie: string = "";
    mascotaArray: Array<any> = [];
}

interface iMascota extends Mascotas {
    listarMascotas(): void;
    listarMascotasPorID(ID: number): void;
    listarMascotasPorNombre(_Nombree: string): void;
    crearMascota(_Id: number, _Nombre: string, _Especie: string): void;
    actualizarMascota(_Id1: number, _Nombre1: string, _Especie1: string): void;
    eliminarMascota(_nombre: string): void;
}

class Repository implements iMascota {
    Id: number = 0;
    Nombre: string = "";
    Especie: string = "";

    //LLENAMOS EL ARRAY
    mascotaArray = [{ Id: 1, Nombre: 'Copito', Especie: 'Canino' },
    { Id: 2, Nombre: 'Motita', Especie: 'Felino' },
    { Id: 3, Nombre: 'Celeste', Especie: 'Ave' }]

    //METODOS IMPLEMENTADOS

    //LISTAR LAS MASCOTAS
    listarMascotas(): void {
        for (let Mascotas of this.mascotaArray) {
            console.log(Mascotas.Id + '\n' + Mascotas.Nombre + '\n' + Mascotas.Especie);
        }
    };

    //LISTAR LAS MASCOTAS POR ID
    listarMascotasPorID(ID: number): void {
        let e: string = "f";

        for (let Mascotas of this.mascotaArray) {
            if (Mascotas.Id == ID) {
                e = 't';
                console.log(Mascotas.Id + '\n' + Mascotas.Nombre + '\n' + Mascotas.Especie);
                break;
            }
            else {
                continue;
            }
        }
        if (e == 'f') {
            window.alert('Lo sentimos la mascota aun no esta registrada!!');
        }
    };

    //LISTAR LAS MASCOTAS POR NOMBRE
    listarMascotasPorNombre(_Nombree: string): void {
        let e: string = "f";

        for (let Mascotas of this.mascotaArray) {
            if (Mascotas.Nombre == _Nombree) {
                e = 't';
                console.log(Mascotas.Id + '\n' + Mascotas.Nombre + '\n' + Mascotas.Especie);
                break;
            }
            else {
                continue;
            }
        }
        if (e == 'f') {
            window.alert('Lo sentimos la mascota aun no esta registrada!!');
        }
    };

    crearMascota(_Id: number, _Nombre: string, _Especie: string): void {
        let e: string = "f";

        for (let Mascotas of this.mascotaArray) {
            if (Mascotas.Id == _Id) {
                e = 't';
                alert('El ID ya existe!!')
                this.listarMascotas();
                break;
            }
            else {
                continue;
            }
        }
        if (e == 'f') {
            this.mascotaArray.push({ Id: _Id, Nombre: _Nombre, Especie: _Especie });
            alert("Mascota registrada exitosamente!!");
            this.listarMascotas();
        }
    };

    actualizarMascota(_Id1: number, _Nombre1: string, _Especie1: string): void {
        let e: string = "f";

        for (let Mascotas of this.mascotaArray) {
            if (Mascotas.Id == _Id1) {
                e = 't';
                this.listarMascotas();
                console.log("-------------------");
                let editarMascota = this.mascotaArray.map(s => s.Id === _Id1 ? { Id: _Id1, Nombre: _Nombre1, Especie: _Especie1 } : s);
                alert('Registro de mascota actualizado exitosamente!!')
                console.log("Array Actualizado: ", editarMascota);
                break;
            }
            else {
                continue;
            }
        }
        if (e == 'f') {
            alert('El ID NO existe!!')
            this.listarMascotas();

        }
    };

    eliminarMascota(_nombre: string): void {
        let nombre = this.mascotaArray.findIndex(s => s.Nombre == _nombre);
        this.listarMascotas();
        console.log("------------------------------");
        this.mascotaArray.splice(nombre, 1);
        alert('Registro de Mascota eliminado exitosamente!!');
        this.listarMascotas();
    };
}

let opc: number = 0;

do {
    opc = Number(window.prompt('PET ANIMALS \n 1. Listar Mascotas \n 2. Listar Mascotas Por ID \n 3. Listar Mascotas Por Nombre \n 4. Crear Mascota \n 5. Actualizar Mascota \n 6. Eliminar Registro Mascota \n 7. Salir'))

    switch (opc) {
        case 1:
            var objRepository = new Repository();
            console.log(objRepository.listarMascotas());
            break;

        case 2:
            var objRepository = new Repository();
            let ID: number = Number(window.prompt('Por favor digite el ID de la mascota por favor!!'))
            console.log(objRepository.listarMascotasPorID(ID))
            break;

        case 3:
            var objRepository = new Repository();
            let _Nombree: string = String(window.prompt('Por favor digite el Nombre de la mascota por favor!!'));
            console.log(objRepository.listarMascotasPorNombre(_Nombree));
            break;

        case 4:
            var objRepository = new Repository();
            let _Id: number = Number(window.prompt('Por favor digite el ID de la mascota por favor!!'));
            let _Nombre: string = String(window.prompt('Por favor digite el Nombre de la mascota por favor!!'));
            let _Especie: string = String(window.prompt('Por favor digite la Especie de la mascota por favor!!'));
            console.log(objRepository.crearMascota(_Id, _Nombre, _Especie));
            break;

        case 5:
            var objRepository = new Repository();
            let _Id1: number = Number(window.prompt('Por favor digite el ID de la mascota por favor!!'));
            let _Nombre1: string = String(window.prompt('Por favor digite el Nombre de la mascota por favor!!'));
            let _Especie1: string = String(window.prompt('Por favor digite la Especie de la mascota por favor!!'));
            console.log(objRepository.actualizarMascota(_Id1, _Nombre1, _Especie1))
            break;

        case 6:
            var objRepository = new Repository();
            let _nombre: string = String(window.prompt('Por favor digite el Nombre de la mascota a eliminar por favor!!'));
            console.log(objRepository.eliminarMascota(_nombre));
            break;

        case 7:
            alert('Un placer!! Vuelva pronto');
            break;

        default:
            alert('Opción incorrecta!!');
            break;
    }
} while (opc != 7)
