---
description: >-
  The following program example demonstrates how various shapes can be drawn by
  a behavior, without the behavior knowing the specific types of shapes,
  essentially polymorphism.
---

# Shape Drawing

The Object-Oriented equivalent found [here](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/object-oriented/polymorphism) was the inspiration for this example.

```
`Declare the contexts of the application.`

App State: context
{
    Should Draw: bool [true];
}.

Draw Plane: context { `Data defining a plane that can be drawn to.` }.

Shape: context
{
    X: int;
    Y: int;
    Height: int [1];
    Width: int [1];
}.

Circle: context Shape.
Rectangle: context Shape.
Triangle: context Shape.
```

```
`Declare the drawing operations for each type of shape.`

Draw Circle on Draw Plane: <circle, plane>?
    `Logic to update the draw plane for the circle.`.
    
Draw Rectangle on Draw Plane: <rectangle, plane>?
    `Logic to update the draw plane for the rectangle.`.
    
Draw Triangle on Draw Plane: <triangle, plane>?
    `Logic to update the draw plane for the triangle.`.
```

```
`Declare a behavior to coordinate the drawing of the shapes to the draw plane.`

Draw {*Shape*} on Draw Plane for proper App State: {shapes, plane, state}?
    Draw: for {shapes, plane, state},
        whenever state(Should Draw),
        foreach shape in shapes?
            await <shape, plane>.
```

```
`Set up the program with a startup operation.`

Main: when initialized?
    await !: App State; as Registration,
    await !: Draw Plane; as Registration,
    
    await !: Circle [ X[20], Y[20] ]; as Registration,
    await !: Rectangle [ Width[10] ]; as Registration,
    await !: Triangle [ X[-20], Y[-20], Height[2] ]; as Registration.
    
    `The behavior will automatically start to run in a loop at this point.`
```
