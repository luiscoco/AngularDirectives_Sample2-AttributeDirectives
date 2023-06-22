# Attribute Directives

https://angular.io/guide/attribute-directives

https://stackblitz.com/~/github.com/luiscoco/AngularDirectives_Sample2-AttributeDirectives

In Angular, attribute directives are a type of directive that allows you to change the behavior or appearance of an HTML element by applying a custom attribute. They are used to add, modify, or remove attributes from elements dynamically.

Attribute directives are denoted by the @Directive decorator in Angular and are applied to elements as attributes in the template. They can be used to listen to events, manipulate the DOM, modify styles, or add additional functionality to elements.

Here's a simple example to demonstrate how attribute directives work in Angular:

Create a new attribute directive:

```typescript
import { Directive, ElementRef, HostListener } from '@angular/core';

@Directive({
  selector: '[highlight]'
})
export class HighlightDirective {
  constructor(private el: ElementRef) {}

  @HostListener('mouseenter') onMouseEnter() {
    this.highlight('yellow');
  }

  @HostListener('mouseleave') onMouseLeave() {
    this.highlight(null);
  }

  private highlight(color: string) {
    this.el.nativeElement.style.backgroundColor = color;
  }
}
```

In this example, we created a directive called HighlightDirective. It listens to the mouseenter and mouseleave events and changes the background color of the element accordingly.

Use the attribute directive in a component's template:

```typescript
<div highlight>
  Hover over me to see the effect!
</div>
```

Here, we apply the highlight attribute directive to a <div> element. When the mouse enters the div, the background color will change to yellow, and when the mouse leaves, it will revert to its original color.

Register the attribute directive in a module:
To make the directive available for use in your application, you need to declare it in an Angular module. Open the module file (e.g., app.module.ts) and add it to the declarations array:

import { NgModule } from '@angular/core';
import { HighlightDirective } from './highlight.directive';

```typescript
@NgModule({
  declarations: [
    HighlightDirective
  ],
  // ...
})
export class AppModule { }
```

By declaring the HighlightDirective in the module, Angular knows that it can be used throughout the application.

When you run the application, you'll see that the div element will change its background color to yellow when you hover over it, thanks to the attribute directive.

This is a basic example to illustrate how attribute directives work in Angular. Depending on your requirements, you can create attribute directives that perform various tasks like controlling visibility, applying animations, validating input, etc. The possibilities are vast, and you can customize the behavior of your elements by creating and using your own attribute directives.


