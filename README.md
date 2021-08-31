# TSTL anim8

Declarations for [anim8](https://github.com/kikito/anim8), a small animation library for LÖVE.


| Command | Description |
|-|-|
| `yarn add -D tstl-anim8` | Install these declarations |
| `yarn add kikito/anim8` | Install anim8 |


Upon installation these declarations can be linked to a _tsconfig.json_ file.

```json
{
    "compilerOptions": {
        "types": [
            "tstl-anim8"
        ]
    }
}
```

And used within any _.ts_ file.

```ts
import * as anim8 from "anim8"

let spritesheet = love.graphics.newImage('path/to/your/spritesheet');
let grid = anim8.newGrid(16,16,spritesheet.getWidth(),spritesheet.getHeight());
let frames = grid.getFrames(1,1, 2,1, 3,1);
let frame_duration = [0.5,0.5,0.5];
let animation = anim8.newAnimation(frames,frame_duration);

love.update = (dt: number) => {
    animation.update(dt);
}

love.draw = () => {
    animation.draw(spritesheet, 100, 100);
}
```

Make sure to append `";./node_modules/?/?.lua"` to your `package.path` in a _conf.ts_ file (this is run first) to assist where Lua looks for modules.

```ts
package.path += ";./node_modules/?/?.lua";
```

Also you need to add `"typescript-to-lua/language-extensions"` to _tsconfig.json_ file.
```json
{
    "compilerOptions": {
        "types": [
            "typescript-to-lua/language-extensions"
        ]
    }
}
```