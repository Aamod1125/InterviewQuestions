Sure! Here’s a list of **Angular interview questions**, grouped by **experience level**:

---

### 🔰 Beginner Level (0–2 years experience)
These test foundational knowledge of Angular concepts.

1. **What is Angular?**
2. **What are components in Angular?**
3. **What is a module in Angular?**
4. **What is data binding? What are its types?**
5. **What is the difference between `ngIf` and `ngFor`?**
6. **What are directives? How many types are there?**
7. **What is the use of `@Input()` and `@Output()`?**
8. **What is the role of services in Angular?**
9. **How does dependency injection work in Angular?**
10. **What are lifecycle hooks? Name a few.**
11. **How do you handle forms in Angular (template-driven vs reactive forms)?**
12. **What is the Angular CLI and why is it useful?**
13. **What is interpolation in Angular?**
14. **What is a pipe in Angular? Can you name a few built-in pipes?**
15. **What are Observables and how are they used in Angular?**

---

### ⚙️ Intermediate Level (2–5 years experience)
Expect questions that cover deeper knowledge and architecture.

1. **How does Angular’s change detection work?**
2. **What are lazy loading and eager loading?**
3. **What is the difference between a pure and impure pipe?**

4. **Explain the role of `ngOnInit`, `ngOnChanges`, and `ngAfterViewInit`.**

~### Answer #### ~ 

Absolutely! Let’s break down the **Angular lifecycle hooks** `ngOnInit`, `ngOnChanges`, and `ngAfterViewInit`, including what they do and how they differ.

---

### 🔁 Lifecycle Hooks Overview

In Angular, lifecycle hooks are special methods you can implement in a component or directive to tap into key moments during its lifespan — from creation to destruction.

---

## ✅ `ngOnInit()`

### **What it is:**
- Runs **once**, after the component’s constructor and after Angular has initialized all data-bound properties.
- Ideal for **initialization logic**, such as fetching data from a service or setting default values.

### **When it runs:**
- After Angular first displays the component's data-bound properties.

### **Usage Example:**
```ts
ngOnInit() {
  this.loadDataFromApi();
}
```

---

## 🔄 `ngOnChanges(changes: SimpleChanges)`

### **What it is:**
- Called **whenever a data-bound `@Input()` property changes**.
- Useful for reacting to changes in parent-provided data.

### **When it runs:**
- **Before `ngOnInit()`** (if there's an initial input)
- **Every time** an `@Input()` value changes afterward

### **Usage Example:**
```ts
@Input() userId: number;

ngOnChanges(changes: SimpleChanges) {
  if (changes['userId']) {
    this.fetchUserDetails(this.userId);
  }
}
```

---

## 👁️‍🗨️ `ngAfterViewInit()`

### **What it is:**
- Called **after the component’s view (and child views)** has been fully initialized.
- Useful when you need to **interact with DOM elements**, use `@ViewChild`, or run animations.

### **When it runs:**
- After the first `ngAfterViewChecked()`

### **Usage Example:**
```ts
@ViewChild('inputRef') inputElement: ElementRef;

ngAfterViewInit() {
  this.inputElement.nativeElement.focus();
}
```

---

## 🔍 Key Differences Summary

| Hook             | Trigger                                 | Use Case                                     | Runs Multiple Times |
|------------------|------------------------------------------|----------------------------------------------|---------------------|
| `ngOnInit()`      | After component initialization            | Initialization logic                         | ❌ No                |
| `ngOnChanges()`   | On any change to `@Input()` properties    | Responding to input property changes         | ✅ Yes               |
| `ngAfterViewInit()` | After component's view is fully initialized | DOM access, `@ViewChild`, animations         | ❌ No                |

---

### Bonus Tip 💡  
- **Don't access DOM in `ngOnInit()`** – do it in `ngAfterViewInit()` to ensure the view is ready.
- If you're not using `@Input()`, `ngOnChanges()` won’t trigger.

---

Want a code demo with all three hooks in action?

5. **How do you optimize performance in Angular apps?**
6. **How does Angular handle routing?**
7. **What is a resolver in Angular routing?**
8. **How do guards work in Angular (CanActivate, CanDeactivate, etc.)?**
9. **What is `ng-content` and how is it used for content projection?**
10. **What is Ahead-of-Time (AOT) compilation?**
11. **What is the difference between `@Injectable()` and `@Component()`?**
12. **Explain the difference between `BehaviorSubject`, `Subject`, and `ReplaySubject`.**
13. **What is ViewEncapsulation in Angular?**
14. **How do you share data between components (Parent ↔ Child, Sibling ↔ Sibling)?**
15. **What are the differences between `Renderer2` and `ElementRef`?**

---

### 🧠 Advanced Level (5+ years experience)
These often focus on architectural decisions, scalability, and performance.

1. **How do you structure a large-scale Angular application?**
2. **How do you manage state in Angular? Have you used NgRx, Akita, or other libraries?**
3. **Explain the Redux pattern and how it's used in Angular.**
4. **What’s the difference between template-driven and reactive forms under the hood?**
5. **How does Angular Universal work (SSR - Server Side Rendering)?**
6. **How do you secure Angular applications (e.g., JWT, XSS, CSRF protection)?**
7. **How do you debug Angular performance issues?**
8. **What is a custom structural directive? Can you give an example?**
9. **How would you migrate a large AngularJS app to Angular 14+?**
10. **How do you implement internationalization (i18n) in Angular?**
11. **How do you handle dynamic component loading?**
12. **How do you use Zones in Angular? What is `NgZone`?**
13. **What is Ivy in Angular? How is it different from the previous compiler?**
14. **How do you test Angular components/services/pipes (unit testing, integration testing)?**
15. **What tools or strategies do you use for code splitting and performance optimization?**

---


### 🧠 Exprience Level (6+ years experience)
These often focus on architectural decisions, scalability, and performance.

1. **Promises and Observables**

`### Answer `

Great question! Both **Promises** and **Observables** are used for handling **asynchronous operations** in JavaScript and Angular — but they work differently and are used in different scenarios.

---

## 📌 Difference Between Promise and Observable

| Feature            | **Promise**                                | **Observable**                             |
|--------------------|---------------------------------------------|---------------------------------------------|
| Emission           | Emits **one** value                        | Can emit **multiple** values over time     |
| Laziness           | **Eager** — executes immediately           | **Lazy** — executes on subscription         |
| Cancelable         | ❌ Not cancelable                          | ✅ Can be unsubscribed                      |
| Operators          | ❌ No operators                            | ✅ Has powerful operators via **RxJS**      |
| Chaining           | ✅ `.then()` / `.catch()`                  | ✅ `.pipe()`, `map()`, `filter()`, etc.     |
| Multicasting       | ❌ No (requires manual logic)              | ✅ Possible via subjects and multicasting   |
| Use Case           | One-time HTTP request, simple async tasks | Reactive programming, streams, events      |

---

## 🔄 Analogy

- **Promise** is like ordering food once. You get it when it’s ready — one time.
- **Observable** is like a subscription to a food box — you keep getting deliveries.

---

## ✅ When to Use What?

| Situation                                  | Use |
|--------------------------------------------|-----|
| One-time HTTP request                      | Either (though Angular HTTP uses Observables) |
| Handling streams of data (e.g., WebSocket) | Observable |
| Need cancellation (e.g., on component destroy) | Observable |
| Simpler, single async task                 | Promise |

---

## 🧪 Code Example

### ✅ Promise:
```ts
const promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Data from promise"), 1000);
});

promise.then(data => console.log(data));
```

### ✅ Observable:
```ts
import { Observable } from 'rxjs';

const observable = new Observable(subscriber => {
  subscriber.next("First data");
  setTimeout(() => subscriber.next("Second data"), 1000);
});

const subscription = observable.subscribe(data => console.log(data));

// Cancel the subscription if needed
// subscription.unsubscribe();
```

---

## 💡 Angular Tip

Angular’s **HttpClient** returns **Observables**, not Promises:

```ts
this.http.get('/api/data')  // returns Observable
  .subscribe(data => console.log(data));
```

You can convert it to a promise if needed using `.toPromise()` (deprecated) or `.firstValueFrom()` in RxJS 7+.

---

Want to see a real Angular example comparing both in a component?

---


2. **How to call multiple APIs in Angular**

Calling **multiple APIs in Angular** can be done in several ways depending on whether you want to:

- Call them **in parallel** (at the same time)  
- Call them **sequentially** (one after the other)  
- Wait for **all** to complete before proceeding  
- **Cancel**, **retry**, or **combine** results

Let’s go through the most common patterns using **RxJS operators**, since Angular's `HttpClient` uses **Observables**.

---

## 🔁 1. **Call Multiple APIs in Parallel** (and wait for all to complete)

Use `forkJoin()` when you want to wait for **all requests to finish** and get all results **together**.

### ✅ Example:

```ts
import { forkJoin } from 'rxjs';

this.apiService1 = this.http.get('/api/user');
this.apiService2 = this.http.get('/api/posts');

forkJoin([this.apiService1, this.apiService2]).subscribe(
  ([userData, postsData]) => {
    console.log('User:', userData);
    console.log('Posts:', postsData);
  }
);
```

📝 `forkJoin()` completes **only when all observables complete**.

---

## 🧬 2. **Call APIs in Sequence** (one after the other)

Use `switchMap`, `concatMap`, or `mergeMap` if the second call depends on the first.

### ✅ Example using `switchMap`:
```ts
import { switchMap } from 'rxjs';

this.http.get('/api/user').pipe(
  switchMap(user => {
    return this.http.get(`/api/posts?userId=${user['id']}`);
  })
).subscribe(posts => {
  console.log('User’s posts:', posts);
});
```

🧠 `switchMap()` cancels previous inner observables if a new value comes in — useful for user typing scenarios.

---

## ⚡ 3. **Call APIs Independently Without Waiting**

If you don’t need to wait for both and can handle them separately:

```ts
this.http.get('/api/user').subscribe(user => {
  console.log('User:', user);
});

this.http.get('/api/posts').subscribe(posts => {
  console.log('Posts:', posts);
});
```

---

## 🔄 Bonus: Combine Results Using `combineLatest`

If you want to react to the **latest values** from multiple APIs (streams), use `combineLatest`:

```ts
import { combineLatest } from 'rxjs';

combineLatest([
  this.http.get('/api/user'),
  this.http.get('/api/notifications')
]).subscribe(([user, notifications]) => {
  console.log('User:', user);
  console.log('Notifications:', notifications);
});
```

---

## 🧪 Example in Angular Service

```ts
getDashboardData(): Observable<any> {
  return forkJoin({
    user: this.http.get('/api/user'),
    stats: this.http.get('/api/stats'),
    messages: this.http.get('/api/messages')
  });
}
```

In component:

```ts
this.dashboardService.getDashboardData().subscribe(data => {
  this.user = data.user;
  this.stats = data.stats;
  this.messages = data.messages;
});
```

---

3. **What happens if one API fails during forkJoin() (parallel API calls)?**

`### Answer`
Great question — and an important one for real-world Angular apps! 👇

---

## 🤯 What happens if one API fails during `forkJoin()` (parallel API calls)?

### 🔥 **If ANY of the API calls fails, `forkJoin()` will throw an error and NOT return any data.**

`forkJoin()` waits for **all observables to complete** successfully.  
If **even one** fails (e.g., `apiService2`), the whole stream **errors out** and lands in the `error` callback.

---

## ✅ Example:

```ts
forkJoin([
  this.http.get('/api/user'),
  this.http.get('/api/posts') // let's say this fails
]).subscribe({
  next: ([user, posts]) => {
    console.log('User:', user);
    console.log('Posts:', posts);
  },
  error: (err) => {
    console.error('One of the APIs failed:', err);
  }
});
```

If `/api/posts` fails → nothing from `/api/user` is returned either.  
Instead, it jumps to the `error` block.

---

## 🛠️ How to Handle Failures Gracefully?

You can catch errors for each observable individually using `catchError()`:

### ✅ Example: Continue if one fails, return fallback value

```ts
import { forkJoin, of } from 'rxjs';
import { catchError } from 'rxjs/operators';

forkJoin([
  this.http.get('/api/user').pipe(
    catchError(err => {
      console.error('User API failed:', err);
      return of(null); // fallback
    })
  ),
  this.http.get('/api/posts').pipe(
    catchError(err => {
      console.error('Posts API failed:', err);
      return of([]); // fallback
    })
  )
]).subscribe(([user, posts]) => {
  console.log('User:', user); // might be null
  console.log('Posts:', posts); // might be []
});
```

---

## 📌 Summary

| Scenario | Behavior |
|----------|----------|
| One API fails | `forkJoin()` errors out, no data returned |
| Use `catchError()` | Lets you handle individual API errors and continue |
| Want partial results | Use `catchError()` with fallback values (like `null` or `[]`) |

---

4. **How to call API After 3 Characters in Angular** 
Nice one — you're talking about **triggering an API call after the user types at least 3 characters**, often used in **search/autocomplete fields**.

Here’s how to do it properly in Angular using **Reactive Forms** + **RxJS operators** like `filter`, `debounceTime`, and `switchMap`.

---

## ✅ Step-by-Step: API Call After 3 Characters in Angular

### 🔹 1. Setup Reactive Form with a Search Field

```ts
import { FormControl } from '@angular/forms';

searchControl = new FormControl('');
```

---

### 🔹 2. Subscribe to Value Changes with Operators

```ts
import { debounceTime, distinctUntilChanged, filter, switchMap } from 'rxjs/operators';

ngOnInit() {
  this.searchControl.valueChanges.pipe(
    debounceTime(300),               // Wait for 300ms pause in typing
    distinctUntilChanged(),          // Only if the value changed
    filter(value => value.length >= 3), // Only if input has 3 or more characters
    switchMap(value => this.http.get(`/api/search?q=${value}`))
  ).subscribe(results => {
    console.log('Search results:', results);
  });
}
```

---

## 💡 Why these operators?

| Operator           | Purpose                                                                 |
|--------------------|-------------------------------------------------------------------------|
| `debounceTime(300)` | Waits for user to stop typing (avoid calling API on every keystroke)  |
| `distinctUntilChanged()` | Prevents duplicate calls if the input didn't change            |
| `filter(value => value.length >= 3)` | Ensures API is called only after 3+ characters     |
| `switchMap()`       | Cancels previous API calls if user keeps typing (common in search UIs) |

---

## 📦 Full Example (Component Snippet)

```ts
@Component({
  selector: 'app-search',
  template: `<input [formControl]="searchControl" placeholder="Search...">`
})
export class SearchComponent implements OnInit {
  searchControl = new FormControl('');

  constructor(private http: HttpClient) {}

  ngOnInit() {
    this.searchControl.valueChanges.pipe(
      debounceTime(300),
      distinctUntilChanged(),
      filter(term => term.length >= 3),
      switchMap(term => this.http.get(`/api/search?q=${term}`))
    ).subscribe(data => {
      console.log('API response:', data);
    });
  }
}
```

---

Want this hooked into a real Angular Material autocomplete or typeahead UI?





