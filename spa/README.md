# spa

The browser side of a single page application: views in templates, links that switch them without reloading, forms that ask an api, and fields its answers fill in.

```
use spa
```

It uses `language` (its `libraries.toml`), installed with it.

| Words | Does | Example |
|---|---|---|
| `web script` | The script of a single page application. Put it in the page with <script def="web script"></script>, and each view in a <template>, like <template def="bmi view"></template>; the view for the address shows in the element that holds the templates. A view is <view path="/bmi" title="BMI calculator" loads="/api/x"> ... </view> (path="*" is any other address; loads asks an api when the view opens). It marks every link to the address with aria-current, sends a <form api="/api/x"> to that api, fills each {name} with the answer (as text, never as HTML) and opens the hidden element around it, keeps a view's <style def="name"></style> to that view, runs a view's <script def="name"></script> with `view` as the view's element (it hears an "answer" event with each answer), shows an error in the view's role="alert" element (or one it adds), and switches views without reloading when a link to "/..." is clicked or Back is pressed. | `serve site page at "/", with <script def="web script"></script> in html site page` |
