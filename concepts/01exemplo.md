# Primeiro exemplo

### Normalmente registramos nossos eventos dessa forma:

```js
document.addEventListener("click", () => console.log("Clicked!"));
```

### Com RxJS você cria um observável dessa forma:

```javascript
import { fromEvent } from "rxjs";

fromEvent(document, "click").subscribe(() => console.log("Clicked!"));
```