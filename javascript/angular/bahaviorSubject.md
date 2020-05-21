# Behavior Subject

Passer des informations a un component très éloigné :

````
@Injectable({
  providedIn: 'root'
})
export class MoodService {

  handleMood$: BehaviorSubject<string> = new BehaviorSubject<string>(null);

  constructor() {
  }

  setMood(message: string) {
    this.handleMood$.next(message);
  }
}
````

Dans mood.component.ts :

````
export class MoodComponent implements OnInit {


  constructor(
    private moodService: MoodService
  ) { }

  ngOnInit(): void {
  }

  iAmOk() {
    this.moodService.setMood('je suis ok');
  }
  iAmNotOk() {
    this.moodService.setMood('je suis pas ok');
  }
  iAmNeutral() {
    this.moodService.setMood('je suis neutre');
  }

}
````

Dans app.component.ts :

````
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss']
})
export class AppComponent implements OnInit{
  title = 'promo3Angular';
  message: string;

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
        tap((message: string) => this.message = message),
      )
      .subscribe();
  }
}

````

suscribe sert à s'abonner a un behavior subject.
