<script>
    let plasma = createPlasma(800, 600);
    let hueShift = 10;

    function createPlasma(w, h) {
        var buffer = new Array(h);

        for (var y = 0; y < h; y++) {
            buffer[y] = new Array(w);

            for (var x = 0; x < w; x++) {

                var value = Math.sin(x / 16.0);
                value += Math.sin(y / 8.0);
                value += Math.sin((x + y) / 16.0);
                value += Math.sin(Math.sqrt(x * x + y * y) / 8.0);
                value += 4; // shift range from -4 .. 4 to 0 .. 8
                value /= 8; // bring range down to 0 .. 1

                buffer[y][x] = value;
            }
        }
        return buffer;
    }

    function drawPlasma(ctx, w, h) {
        var img = ctx.getImageData(0, 0, w, h);

        for (var y = 0; y < h; y++) {

            for (var x = 0; x < w; x++) {

                var hue = hueShift + plasma[y][x] % 1;
                var rgb = HSVtoRGB(hue, 1, 1);
                var pos = (y * w + x) * 4;
                img.data[pos] = rgb.r;
                img.data[pos + 1] = rgb.g;
                img.data[pos + 2] = rgb.b;
            }
        }
        ctx.putImageData(img, 0, 0);
    }

    /* copied from stackoverflow */
    function HSVtoRGB(h, s, v) {
        var r, g, b, i, f, p, q, t;

        i = Math.floor(h * 6);
        f = h * 6 - i;
        p = v * (1 - s);
        q = v * (1 - f * s);
        t = v * (1 - (1 - f) * s);
        switch (i % 6) {
            case 0: r = v, g = t, b = p; break;
            case 1: r = q, g = v, b = p; break;
            case 2: r = p, g = v, b = t; break;
            case 3: r = p, g = q, b = v; break;
            case 4: r = t, g = p, b = v; break;
            case 5: r = v, g = p, b = q; break;
        }
        return {
            r: Math.round(r * 255),
            g: Math.round(g * 255),
            b: Math.round(b * 255)
        };
    }

    function animate(ctx, lastFrameTime) {
        let time = new Date().getTime();
        let delay = 42;

        if (lastFrameTime + delay < time) {
            hueShift = (hueShift + 0.02) % 1;
            drawPlasma(ctx, 800, 600);
            //drawBorder();
            lastFrameTime = time;
        }
console.log('asdasd')
        requestAnimationFrame(function () {
            animate(ctx, lastFrameTime);
        });
    }

    export default {
        // Gets us the provider property from the parent <game-canvas> component.
        inject: ['provider'],

        props: {
            // Start coordinates (percentage of canvas dimensions).
            width: {
                type: Number,
                default: 0
            },
            height: {
                type: Number,
                default: 0
            }
        },

        data() {
            return {
                // We cache the dimensions of the previous
                // render so that we can clear the area later.
                oldBox: {
                    x: null,
                    y: null,
                    w: null,
                    h: null
                },
                redraw: 1
            }
        },

        computed: {},
        render() {
            // Since the parent canvas has to mount first, it's *possible* that the context may not be
            // injected by the time this render function runs the first time.
            if (!this.provider.context) {
                return;
            }

            const ctx = this.provider.context;
            /*
                        ctx.beginPath();
                        // Clear the old area from the previous render.
                        // Clear the area for the text.
                        // Draw the new rectangle.
                        ctx.rect(0, 0, 200, 200);
                        ctx.fillStyle = this.color;
                        ctx.fill();*/

            let r, g, b, a;

            /*      for (let x = 0; x < this.width; x++) {
                      for (let y = 0; y < this.height; y++) {
                          r = (Math.random() * 255);
                          g = (Math.random() * 255);
                          b = (Math.random() * 255);
                          a = 255;
                          ctx.fillStyle = "rgba(" + r + "," + g + "," + b + "," + (a / 255) + ")";
                          ctx.fillRect(x, y, 1, 1);
                      }
                  }
                  */
            let w = 800, h = 600
            var img = ctx.getImageData(0, 0, w, h);
                    ctx.fillRect(x, y, 1, 1);

            for (var y = 0; y < h; y++) {

                for (var x = 0; x < w; x++) {

                    let hue = hueShift + plasma[y][x] % 1;
                    let rgb = HSVtoRGB(hue, 1, 1);
                    let pos = (y * w + x) * 4;
                    img.data[pos] = rgb.r;
                    img.data[pos + 1] = rgb.g;
                    img.data[pos + 2] = rgb.b;
                }
            }
            ctx.putImageData(img, 10, 10);
            //animate(ctx, 0);
        },
        methods: {
            handleInput(event) {
                this.redraw += 1;
            },
            handleMouse(event) {
            },

        },
        mounted() {
            window.addEventListener('keydown', this.handleInput);
            window.addEventListener('mousemove', this.handleMouse);
        },
        beforeDestroy() {
            window.removeEventListener('keydown', this.handleInput);
            window.removeEventListener('mousemove', this.handleMouse);
        },

    }
</script>
