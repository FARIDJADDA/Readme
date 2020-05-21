# Unsubscribe

On va gérer le désabonnement. Quand on s'abonne, on reste abonné jusqu'a ce que l'application angular fonctionne.
Pour éviter les bugs, on va faire en sorte quand quand le component ne s'affiche plus a l'écran on est plus abonné.
Quand le component n'a plus besoin d'etre la il va s'auto detruire `onDestroy`

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
  ) {
  }

  ngOnInit(): void {
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

On a dit a ngOnInit() qu'on reste abonné tant que destroy ne vaut rien `takeUntil`.
Et lui a indiqué de s'arreter quand le désabonnement est fait `.complete`
