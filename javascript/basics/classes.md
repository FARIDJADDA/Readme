# Les classes

Une classe permet de faciliter le code. Elle fournit uniquement une syntaxe plus simple pour créer des objets et manipuler l'héritage.

## Exemples

````
// Dans model :

export interface TeamModel {
    id?: number;
    name: string;
    roomsNumbers?: number;
    pool?: boolean;
    rooms?: RoomModel[];
    isValidated?: boolean;
}

export class HotelClass {
  id?: number;
  name?: string;
  roomsNumbers?: number;
  pool?: boolean;
  isValidated?: boolean;

  constructor (
    id: number,
    name: string,
    pool?: boolean,
    roomsNumbers?: number,
    isValidated?: boolean,
    ) {
        this.id = id;
        this.name = name;
        this.roomsNumbers = roomsNumbers;
        this.pool = pool;
        this.isValidated = isValidated;
    }
}

const myHotel = new HotelClass();
console.log(myHotel);

// Dans server.ts

app.get('/', async function (req, res) {
    const myHotel = new HotelClass(12, 'hotel des fleurs');
    console.log(myHotel.id);
    res.send(myHotel);
}
````

## Autres façon de faire : 

````
// Dans model :

export interface HotelModel {
    id?: number;
    name: string;
    roomsNumbers?: number;
    pool?: boolean;
    rooms?: RoomModel[];
    isValidated?: boolean;
}

export class HotelClass {
  id?: number;
  name?: string;
  roomsNumbers?: number;
  pool?: boolean;
  isValidated?: boolean;

  constructor (hotel: HotelModel) {
    Object.asssign(this, hotel)
    }
}

const myHotel = new HotelClass();
console.log(myHotel);

// Dans server.ts

app.get('/', async function (req, res) {
    const myHotel = new HotelClass({id: 12, name: 'hotel des fleurs'});
    console.log(myHotel.id);
    res.send(myHotel);
}
````

## En utilisant des fonctions :

````
// Dans model :

export interface HotelModel {
    id?: number;
    name: string;
    roomsNumbers?: number;
    pool?: boolean;
    rooms: RoomModel[];
    isValidated?: boolean;
}

export class HotelClass {
    id?: number;
    name?: string;
    roomsNumbers?: number;
    pool?: boolean;
    isValidated?: boolean;
    rooms: RoomModel[];

  constructor (hotel: HotelModel) {
    this.rooms = hotel.rooms;
    Object.asssign(this, hotel)
    }
    
    calculateRoomNumbers(): HotelClass {
        this.roomNumbers = this.rooms.length;
        return this;
    }
    destroyPool(): HotelClass  {
        this.pool = false;
        return this;
    }
    createPool(): HotelClass  {
        this.pool = true;
        return this;
     }
}

const myHotel = new HotelClass();
console.log(myHotel);

// Dans server.ts

app.get('/', async function (req, res) {
    const myHotel = new HotelClass({id: 12, name: 'hotel des fleurs', rooms[]});
    myHotel
        .calculateRoomNumbers()
        .createPool()
    res.send(myHotel);
}
````

## l'héritage :

````
// Dans model :

export interface HotelModel {
    id?: number;
    name: string;
    roomsNumbers?: number;
    pool?: boolean;
    rooms: RoomModel[];
    isValidated?: boolean;
}

export class HotelClass {
    id?: number;
    name?: string;
    roomsNumbers?: number;
    pool?: boolean;
    isValidated?: boolean;
    rooms: RoomModel[];

  constructor (hotel: HotelModel) {
    this.rooms = hotel.rooms;
    Object.asssign(this, hotel)
    }
    
    calculateRoomNumbers(): HotelClass {
        this.roomNumbers = this.rooms.length;
        return this;
    }
    destroyPool(): HotelClass  {
        this.pool = false;
        return this;
    }
    createPool(): HotelClass  {
        this.pool = true;
        return this;
     }
}

export interface LuxHotelModel extends HotelModel {
    numberOfStars?: number;
    numberOfRoofTops?: number;
}

export class LuxHotelClass extends HotelClass {
     numberOfStars?: number;
     numberOfRoofTops?: number;

      constructor (hotel: LuxHotelModel) {
        super(hotel);
        this.numberOfStars = hotel.numbersOfStars || 1;
        this.numberOfRoofTops = hotel.numberOfRoofTops || 1;
        }
}

// Dans server.ts

app.get('/', async function (req, res) {
    const myHotel = new LuxHotelClass({
        id: 12, 
        name: 'hotel des fleurs', 
        rooms[], 
        numberOfRoofTops: 2;
        numberOfStars: 4,
    });
    myHotel
        .calculateRoomNumbers()
        .createPool()
    res.send(myHotel);
}
````

## Avec les rooms :

````
export interface RoomModel {
    roomName: string;
    size: number;
    id: number;
}

export class RoomClass implements RoomModel {
    roomName: string;
    size: number;
    id: number;

    constructor(id: number, roomName: string = '', size: number = 0,) {
        this.roomName = roomName;
        this.size = size;  
        this.id = id;
    }
}

app.get('/', async function (req, res) {
    const myRoom = new RoomClass(12)
    res.send(myRoom);
}

````

* extends : Le mot-clé extends est utilisé dans les déclarations et expressions de classes afin de signifier qu'un type représenté par une classe hérite d'un autre type.

