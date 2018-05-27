# flu.framework 0.0.7
#### A Simple Component JSF
```javascript
class InputOutput extends flu.component {

    model () {
        this.prop = "--Your Name--";
        this.title = "Hello world! I'm ";
    }

    view () {
        return {{
            h1(hello)
               span(out)>{this.prop}
            input[type=text](in)
        }}
    }

    controller(data) {
        const reg = flu.reg(this);

        reg.it("hello").innerBefore(data.title);

        reg.onEvent.keydown({
            target: "in",
            run: function () {
                let val = this.value("in").get();

                this.it("out").inner(val);
            }
        });
    }

}

flu.class(InputOutput).render(".app");
```

[DEMO](https://philippzhulev.github.io/flu/)

