# Faire un get

Quand on veut communiquer avec une api en angular il faut faire un service.

1. On créer un service hôtel `ng g s services/hotel`
2. Dans le fichier hotel.service.ts :

````
@Injectable({
  providedIn: 'root'
})
export class HotelService {

  root: string = environment.api;

  constructor(
    private httpClient: HttpClient,
  ) {
  }
  getHotelById$(hotelId: string): Observable<HotelModel> {
    return this.httpClient.get(this.root + hotelId) as Observable<HotelModel>;
    }

    getAllHotels$(): Observable<HotelModel[]> {
    return this.httpClient.get(this.root + 'hostels') as Observable<HotelModel[]>;
    }
}
````
3. Créer le model HotelModel dans models
4. Aller dans app.component.ts et faire l'appel :

````
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss']
})
export class AppComponent implements OnInit, OnDestroy{
  title = 'promo3Angular';
  message: string;
  destroy$: Subject<boolean> = new Subject();

  allRoutes: MenuModel[] = this.menuService.allRoutes;
  age = 54;

  constructor(
    private menuService: MenuService,
    private moodService: MoodService,
    private hotelService: HotelService,
  ) {
  }

  ngOnInit(): void {

    this.hotelService.getAllHotels$()
      .pipe(
        tap(x => console.log(x)),
      )
      .subscribe();

    this.moodService.handleMood$
      .pipe(
        takeUntil(this.destroy$),
        tap((message: string) => this.message = message),
      )
      .subscribe();
  }

  ngOnDestroy(): void {
    this.destroy$.next(true);
    this.destroy$.complete();
  }
}
````

5. Dans app.module.ts, on fait l'import :

````
@NgModule({
  declarations: [
    AppComponent
  ],
    imports: [
        BrowserModule,
        AppRoutingModule,
        MainMenuModule,
        MoodModule,
        HttpClientModule,
    ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
````
