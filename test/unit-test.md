# Unit Test

## When the Coverage seems fucked up

### Remove SourceMaps

The option `--sourcemaps=false` or `-sm=false` can help the debug when an error occur.  
Nevertheless it can be responsible for weird coverage report (which make it innacurate).

Remove this option from the `ng test` command.

## Error: 1 timer(s) still in the queue.

To fix it, you must use the fakeAsync syntax with a tick and wait for stable fixture.

```javascript
it('should do ...', fakeAsync(() => {

  // Do some stuff here
    
  tick(500);
  fixture.whenStable().then(() => {
  
    // Add your expectation here
      
  });
}));
```

## Testing private methods

No, you can't.

## Spying private methods call

Use the `spyOn<any>` syntax and save the Spy in a variable.  
The expectation should be directly the Spy.

```javascript
it('should ...', () => {
  const spy: Spy = spyOn<any>(component, 'privateMethod');
  component.ngOnInit();
  expect(spy).toHaveBeenCalled();
});
```

## How to test an event in a directive

Check out this example where we want to `preventDefault()` on the event.

```javascript
@HostListener('click', ['$event'])
public onClick(event: any): void {
  event.preventDefault();
}
```

To test it, you must create your own directive and event objects.  
Then spy on the event's `preventDefault()` method.  
Simulate the HostListener and finally expect the call.

```javascript
it('should prevent default on event', () => {
  const directive: ExampleDirective = new ExampleDirective();
  const clickEvent: MouseEvent = new MouseEvent('click', null);
  spyOn(clickEvent, 'preventDefault');
  fixture.detectChanges();
  directive.onClick(clickEvent);
  expect(clickEvent.preventDefault).toHaveBeenCalled();
}
```
