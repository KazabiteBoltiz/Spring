# Spring Math Interpolator

## Motivation:
- Existing spring systems absolutely munch on runtime, running every frame even when not being used.
- This implementation of a spring math interpolator works on the built-in methods os.clock(), calculates passed time since last _index call and adjusts the spring output accordingly.
- Furthermore, it supports timeskips, and allows impulse velocities to be instantaneously added to the calculations.

- This system helps with creating continuously running animation systems, like viewmodels, hair simulations, etc. Due to its lazy behavior, it only runs the calculations when the _Position value is fetched. This makes it ideal to use for procedural animations. 

## Usage:
- ### **`Spring.new(defaultValue) -> SpringObject`**
  The `defaultValue` supports `Vector2`, `Vector3`, `float`, `int`. This creates a springObject and time is instantiated to 0. This is marked as the point of reference for future calls.

- ### **`SpringObject:Impulse(impulseVelocity) -> Void`**
  Applies a velocity impulse on a springObject and continues easing towards the latest set _Target.

- ### **`SpringObject.Target -> type(defaultValue)`**
  Returns the existing _Target variable. Can be set to for updating the Target that you want the spring to stretch towards.

- ### **`SpringObject.Damper`**
  Returns the damping factor _Damper. Can be set to for updating the default damper value. This controls the "swing" for the instantaneous _Position to reach _Target.

- ### **`SpringObject.Speed`**
  Returns the spring simulation time multiplier _Speed, Can be set to for updating the default Speed. All _Position outputs are boosted by this variable. It is independent of _Damper.

- ### **`SpringObject.Position -> type(defaultValue)`**
  This is the output of the spring interpolator which is guaranteed to be safe to use at all times.
