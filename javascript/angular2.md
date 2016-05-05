**`目录`**

- [1.html5标签](#html5标签)
	+ [语义化标签](#语义化标签)

---
```html5
<head>
  <script type="text/typescript">
    import {Component} from "angular2/core";
    import {bootstrap} from "angular2/platform/browser";

    @Component({
      selector:"ez-app",
      templateUrl : "src/mobile.html"
    })
    class EzApp{}

    bootstrap(EzApp);
  </script>
<head>
<body>
  <ez-app></ez-app>
</body>
```
