## What is angular js

```Angular 2 is an open source JavaScript framework to build web applications in HTML and JavaScript```

### What is difference between angularjs and Angular2 and above version

[https://www.talkingdotnet.com/difference-between-angular-1-x-and-angular-2/](difference)

### How to install & Also how to install specific version of the angular

Install :
```
install node
npm install -g @angular/cli
ng new my-first-app
npm start

```
Install specific version:
```
npm uninstall -g @angular/cli
npm cache clean 
npm install -g @angular/cli@17.1.0

```

### File stracture of angular
[https://angular.dev/reference/configs/file-structure](file stracture)



For a **12+ years experienced Angular developer**, interview questions typically focus on **architecture, performance optimization, state management, security, scalability, and deep internals** of Angular. Below are some advanced Angular interview questions along with their answers.

$${\color{red} advanced - Angular - interview -questions- along -with -their- answers }$$

---

## **1. Angular Internals & Change Detection**
### **Q1: How does Angular’s change detection work internally?**
**Answer:**  
Angular uses a **zone-based change detection mechanism**. It checks the component tree to detect changes in the UI.

- **Zone.js** patches async APIs (e.g., `setTimeout`, `HTTP requests`) to detect changes.
- **Change Detection Strategy:**
  1. **Default** – Checks entire component tree.
  2. **OnPush** – Only checks when `@Input()` changes or manually triggered.

#### **Example:**
```typescript
@Component({
  selector: 'app-example',
  template: `<p>{{data.value}}</p>`,
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class ExampleComponent {
  @Input() data!: { value: string };
}
```
- With **OnPush**, Angular updates only when `@Input()` reference changes.

---

## **2. RxJS & Observables**

### **Q2: What is the difference between `switchMap`, `mergeMap`, `concatMap`, and `exhaustMap`?**
**Answer:**  
All these operators transform one observable into another, but they behave differently:

| Operator  | Behavior |
|-----------|----------|
| **switchMap** | Cancels previous request and starts a new one (best for API calls). |
| **mergeMap** | Runs multiple requests in parallel (no cancellation). |
| **concatMap** | Runs requests sequentially, waiting for the previous one to complete. |
| **exhaustMap** | Ignores new requests while a current request is ongoing. |

#### **Example:**
```typescript
fromEvent(button, 'click').pipe(
  switchMap(() => http.get('/api/data'))
).subscribe(console.log);
```
**Scenario:**
- **Use `switchMap`** for live search (cancels old requests).
- **Use `mergeMap`** for multiple independent API calls.
- **Use `concatMap`** for step-by-step workflows.
- **Use `exhaustMap`** for login buttons to prevent duplicate requests.

---

## **3. State Management**
### **Q3: How would you manage state in a large Angular application?**
**Answer:**  
There are different ways to manage state:
1. **Service-based state management** – Using `BehaviorSubject` in services.
2. **NgRx (Redux for Angular)** – Best for large-scale applications.
3. **Component Store (NgRx alternative)** – Lightweight, ideal for feature-based state.
4. **LocalStorage or IndexedDB** – For persistent state.

#### **Example using BehaviorSubject:**
```typescript
@Injectable({ providedIn: 'root' })
export class StateService {
  private count$ = new BehaviorSubject<number>(0);
  
  getCount(): Observable<number> {
    return this.count$.asObservable();
  }

  updateCount(value: number): void {
    this.count$.next(value);
  }
}
```
This approach avoids unnecessary global state libraries for small apps.

---

## **4. Angular Directives**
### **Q4: How do you create a custom structural directive?**
**Answer:**  
A **structural directive** (`*directive`) modifies the DOM by adding or removing elements.

#### **Example: Custom `*ifRole` directive**
```typescript
@Directive({
  selector: '[ifRole]'
})
export class IfRoleDirective {
  constructor(private templateRef: TemplateRef<any>, private viewContainer: ViewContainerRef) {}

  @Input() set ifRole(role: string) {
    if (role === 'admin') {
      this.viewContainer.createEmbeddedView(this.templateRef);
    } else {
      this.viewContainer.clear();
    }
  }
}
```
**Usage:**
```html
<div *ifRole="'admin'">Admin Content</div>
```

---

## **5. Performance Optimization**
### **Q5: How do you optimize an Angular application?**
**Answer:**  
1. **Use OnPush Change Detection** to reduce checks.
2. **Lazy Load Modules** using `loadChildren`.
3. **Optimize RxJS Operators** (`debounceTime`, `take`, `switchMap`).
4. **Avoid Unnecessary DOM Updates** (`trackBy` in `*ngFor`).
5. **Use Web Workers** for heavy computations.
6. **Preload & Prefetch Assets** for better performance.

#### **Example: Using trackBy in *ngFor**
```html
<li *ngFor="let user of users; trackBy: trackByFn">{{ user.name }}</li>
```
```typescript
trackByFn(index: number, user: User) {
  return user.id; // Prevents unnecessary DOM updates
}
```

---

## **6. Dependency Injection (DI) & Providers**
### **Q6: What are the different types of providers in Angular?**
**Answer:**  
Angular provides **3 types of dependency injection providers**:

| Provider Type | Scope | Example |
|--------------|-------|---------|
| **`providedIn: 'root'`** | Singleton (global) | `@Injectable({ providedIn: 'root' })` |
| **Module-Level Providers** | Available in one module | `{ provide: API_URL, useValue: 'https://api.example.com' }` in `providers[]` |
| **Component-Level Providers** | Created per component instance | `providers: [SomeService]` inside `@Component({ ... })` |

---

## **7. Angular Security**
### **Q7: How do you prevent XSS and CSRF attacks in Angular?**
**Answer:**
1. **Prevent XSS (Cross-Site Scripting)**:
   - Use Angular’s **sanitization APIs** (`DomSanitizer`).
   - Avoid **`[innerHTML]`** and use `bypassSecurityTrustHtml` cautiously.

2. **Prevent CSRF (Cross-Site Request Forgery)**:
   - Use **SameSite cookies**.
   - Implement **CSRF tokens** in API requests.

#### **Example: Sanitizing URLs**
```typescript
constructor(private sanitizer: DomSanitizer) {}

safeUrl = this.sanitizer.bypassSecurityTrustUrl('javascript:alert("XSS Attack")'); // Risky! Avoid if possible
```

---

## **8. Lazy Loading & Module Federation**

### **Q8: How do you implement lazy loading in Angular?**
**Answer:**  
Lazy loading improves performance by loading modules **only when needed**.

#### **Example: Lazy Load a Module**
```typescript
const routes: Routes = [
  { path: 'dashboard', loadChildren: () => import('./dashboard/dashboard.module').then(m => m.DashboardModule) }
];
```
**Benefits:**
- Reduces initial bundle size.
- Improves application speed.

---

## **9. Server-Side Rendering (SSR) with Angular Universal**

### **Q9: What is Angular Universal, and why use it?**
**Answer:**
Angular Universal is used for **Server-Side Rendering (SSR)**.

**Advantages:**
- **Improves SEO** for crawlers like Google.
- **Faster initial page load** by rendering on the server.
- **Better performance on low-powered devices**.

#### **Basic Setup (SSR in Angular)**
```bash
ng add @nguniversal/express-engine
ng build && ng run my-app:server
```

---

## **10. Monorepo & Micro Frontends**
### **Q10: How do you structure a monorepo for a large Angular project?**
**Answer:**  
Use **Nx (Nrwl)** or **Lerna** to manage multiple Angular apps/libraries in a single repository.

```bash
npx create-nx-workspace myworkspace --preset=angular
```
**Benefits:**
- Code sharing across teams.
- Enforces **modular architecture**.

---

These are some of the **most advanced Angular interview questions** for **12+ years experienced developers**. Would you like **hands-on coding scenarios** or **system design questions** as well? 🚀

