# IFW Editor

A small single-file editor for **IFW (Image For Web)**, one of the WebLang languages (`.ifw`). Write IFW on one side, see the drawing update on the other, and download it as **SVG**, **PNG** or **JPG**.

The drawing code is the `compileIFW` function from the WebLang IDE (`IDE.html` in The-WebLang), copied unchanged. The editor around it is new.

## Run it

Open `index.html` in a desktop browser. No install, no server, no internet needed. It was tested in headless Chrome only. Phones and Safari were not tested.

## Use it

1. Type IFW in the code box (right side in the Arabic layout). The drawing updates as you type.
2. Pick a ready example from the first drop-down if you want a start.
3. Pick the PNG/JPG size (1x, 2x, 4x), then press the download button you want.
4. "حفظ ملف ifw" saves your code as `image.ifw`.

Your last code is kept in the browser (localStorage) and comes back when you reopen the file in the same browser.

## IFW syntax supported

One shape per line: `shape: properties`. Lines starting with `#` are comments. Properties are `name=value` with no spaces or commas inside a value (so `c=#ff4d5e` or `c=red`, not `rgb(1,2,3)`). Default color is `#333333`.

| Shape | Example | Notes |
|---|---|---|
| `circle` | `circle: r=40 c=blue` | `r` radius, default 50 |
| `square` | `square: s=80 c=#7c5cff` | `s` side, default 100 |
| `rect` | `rect: w=120 h=50 c=#00d4ff` | default 100 x 50 |
| `triangle` | `triangle: s=80 c=#38e08a` | `s` size, default 80 |
| `star` | `star: s=45 c=#ffd34d` | 5 points, `s` is the outer radius, default 50 |
| `line` | `line: from(0,230) to(400,230) c=#38e08a w=4` | needs `from(x,y)` and `to(x,y)`, `w` thickness, default 2 |
| `polygon` | `polygon: points(0,260 90,130 170,260) c=#2a2058` | at least 3 points |
| `text` | `text: "HZM.Dev" x=130 y=200 c=#8ecbff size=26` | text in quotes, `size` default 16, Arial |
| `path` | `path: M0,0 L50,50 c=red` | outline only, 2px stroke |

Placing: give `x` and `y` for exact positions. Without them, shapes go left to right with a 10px gap, bottom-aligned. There is no background, so add a big `rect` first if you want one.

Unknown shapes or bad lines are skipped, and the editor shows the compiler's warning under the preview.

## Export

| Button | Result |
|---|---|
| SVG | `image.svg`, the drawing as vector (no scaling needed) |
| PNG | `image.png`, transparent background, size 1x / 2x / 4x of the drawing |
| JPG | `image.jpg`, white background (JPG has no transparency), same size choices |

PNG and JPG are made by drawing the SVG on a canvas, so the browser's own limits on canvas size apply to very large drawings. Text uses Arial, so it looks as the viewer's device renders Arial.

## Not included

- No video making or video export. This editor makes still images only.
- No other WebLang languages (BTW, STW, MTWC and the rest). Only IFW.
- No undo history beyond the browser's own text-box undo.
- Not a full SVG editor: only the shapes in the table above.
