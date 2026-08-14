<div align="center">
    <h1 style="border-bottom: none; margin-bottom: 0;">KACUBED</h1>
    A 3D ECS Game Engine
</div>

## About the Project

KACUBED is a 3D game library for the web, designed to feel like a game while creating exciting and immersive experiences.

## Examples

```js
// start a game
kacubed();

// load a model
loadModel("monkey", "models/monkey.obj");

// add the model to the game world
add([
    pos(0, 0, -3),
    model("monkey"),
]);
```

Game objects are composed from simple, powerful components:

```js
// add a game object to the world from a list of components
const player = add([
    pos(0, 0, -3), // it has a world coordinate
    model("monkey"), // it renders as a model
    health(8), // it has 8 health points
    // give it tags for easier group behaviors
    "monke",
    // give plain object field for associated data
    {
        dir: vec3(-1, 0, 0),
        dead: false,
        speed: 240,
    },
]);
```

Blocky imperative syntax for describing behaviors

```js
// add death on fall
player.onUpdate(() => {
    if (player.pos.y >= height()) {
        destroy(player);
    }
});

// all objects with the "enemy" tag will move to the left
onUpdate("enemy", (enemy) => {
    enemy.move(-400, 0, 0);
});

// move up 100px per second every frame when the "w" key is held down
onKeyDown("w", () => {
    player.move(0, 100, 0);
});
```