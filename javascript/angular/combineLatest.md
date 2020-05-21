# Combine Latest

Pour éviter de faire deux subscribe , on peut faire deux abonnements en meme temps. (comme PromiseAll)

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

    combineLatest([
      this.hotelService.getAllHotels$()
        .pipe(
          tap(x => console.log(x)),
        ),
      this.moodService.handleMood$
        .pipe(
          tap((message: string) => this.message = message),
        )
    ])
      .pipe(
        takeUntil(this.destroy$),
      )
      .subscribe();
  }

  ngOnDestroy(): void {
    this.destroy$.next(true);
    this.destroy$.complete();
  }
}
````

on a également mis qu'un seul takeUntil.
