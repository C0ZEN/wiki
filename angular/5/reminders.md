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

__Template__

```
<btn on-click="onClick()"></btn>
```

__Component__

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
