# Reminders

## Binding targets

### Property

```
<btn [label]="myLabel"></btn>

<btn bind-label="myLabel"></btn>
```

### Event

```
<btn (click)="onClick()"></btn>

<btn on-click="onClick()"></btn>
```

### Two-way

```
<btn [(item)]="myItem"></btn>

<btn bindon-item="myItem"></btn>
```

### Attribute

```
<btn [attr.aria-label]="help"></btn>
```

### Class

```
<btn [class.special]="isSpecial"></btn>
```

### Style

```
<btn [style.color]="isSpecial ? 'red' : 'green'"></btn>
```

## Canonical form

- `bind-`
- `on-`
- `bindon-`

## One-time string initialization

```
<btn is-fat="{{isFat}}"></btn>
```

## Property binding or interpolation ?

```
<p><img src="{{heroImageUrl}}"> is the <i>interpolated</i> image.</p>
<p><img [src]="heroImageUrl"> is the <i>property bound</i> image.</p>
```

## Custom events with EventEmitter

### DOM 

```
<btn-component click-event="onClick($event)"></btn-component>
```

### Component

**Template**

```
<btn on-click="onClick()"></btn>
```

**Component**

```
@Output() public clickEvent: EventEmitter<any> = new EventEmitter();

public onClick() {
  this.clickEvent.emit('anything');
}
```

## Built-in attribute directives

- `bindon-ngClass`
- `bindon-ngStyle`
- `bindon-ngModel`

### Lifecycle sequence (component/directive)

**ngOnChanges()**

Respond when Angular (re)sets data-bound input properties.  
The method receives a SimpleChanges object of current and previous property values.  
Called before ngOnInit() and whenever one or more data-bound input properties change.

**ngOnInit()**

Initialize the directive/component after Angular first displays the data-bound properties and sets the directive/component's input properties.  
Called once, after the first ngOnChanges().

**ngDoCheck()**

Detect and act upon changes that Angular can't or won't detect on its own.  
Called during every change detection run, immediately after ngOnChanges() and ngOnInit().

**ngAfterContentInit()**

Respond after Angular projects external content into the component's view / the view that a directive is in.  
Called once after the first ngDoCheck().

**ngAfterContentChecked()**

Respond after Angular checks the content projected into the directive/component.  
Called after the ngAfterContentInit() and every subsequent ngDoCheck().

**ngAfterViewInit()**

Respond after Angular initializes the component's views and child views / the view that a directive is in.  
Called once after the first ngAfterContentChecked().

**ngAfterViewChecked()**

Respond after Angular checks the component's views and child views / the view that a directive is in.  
Called after the ngAfterViewInit and every subsequent ngAfterContentChecked().

**ngOnDestroy()**

Cleanup just before Angular destroys the directive/component.  
Unsubscribe Observables and detach event handlers to avoid memory leaks.  
Called just before Angular destroys the directive/component.

## Watch event on specific element

Let's take for example the scroll event.

Create a reference variable.

```html
<div #overflowContent></div>
```

Create a @ViewChild.

```javascript
@ViewChild('overflowContent') public overflowContent: ElementRef;
```

Create an from event observable.

```javascript
private scrollEvent: Subscription;
public ngAfterViewInit(): void {
  this.scrollEvent = fromEvent(this.overflowContent.nativeElement, 'scroll').subscribe(() => {
    // Do your stuff here
  });
}
```
