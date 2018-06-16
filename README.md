# mosaic-node-generator-example

This is an example in order to show how to use the [mosaic-node-generator](https://github.com/Dellos7/mosaic-node-generator) module.
See the [README](https://github.com/Dellos7/mosaic-node-generator/blob/master/README.md) in order to learn how to use it.

# Download and installation

First, you need to have installed the following:
- [Node.js](https://nodejs.org/es/)
- [Git](https://git-scm.com/downloads)

Then, download the Github repo and install dependencies:

```bash
git clone https://github.com/Dellos7/mosaic-node-generator-example.git
cd mosaic-node-generator-example
npm install
```

# Run the example

```bash
npm run mosaic
```

or

```bash
node index.js
```

When execution ends, you will have your generated mosaic image inside the `outputs` folder.

# Results samples

## Input image ([`input.jpg`](https://github.com/Dellos7/mosaic-node-generator-example/blob/master/input.jpg))

[<img src="https://github.com/Dellos7/mosaic-node-generator-example/raw/master/input.jpg" width="300" />](https://github.com/Dellos7/mosaic-node-generator-example/raw/master/input.jpg")

## Outputs

Output using **100 rows** and **100 columns** as input and and **30x30 cell width and height** ([`output_rc-100_30x30.jpg`](https://github.com/Dellos7/mosaic-node-generator-example/blob/master/outputs/output_rc-100_30x30.jpg))

[<img src="https://github.com/Dellos7/mosaic-node-generator-example/raw/master/outputs/output_rc-100_30x30.jpg" width="300" />](https://github.com/Dellos7/mosaic-node-generator-example/raw/master/outputs/output_rc-100_30x30.jpg)

Code:

```javascript
var mng = require('mosaic-node-generator');

mng.mosaic(
    'input.jpg',
    'pictures',
    30,
    30,
    100,
    100,
    null,
    'thumbnails_30',
    true
);
```

Output using **80 rows** and **80 columns** as input and **30x30 cell width and height** ([`output_rc-80_30x30.jpg`](https://github.com/Dellos7/mosaic-node-generator-example/blob/master/outputs/output_rc-80_30x30.jpg))

[<img src="https://github.com/Dellos7/mosaic-node-generator-example/raw/master/outputs/output_rc-80_30x30.jpg" width="300" />](https://github.com/Dellos7/mosaic-node-generator-example/raw/master/outputs/output_rc-80_30x30.jpg)

Code:

```javascript
var mng = require('mosaic-node-generator');

mng.mosaic(
    'input.jpg',
    'pictures',
    30,
    30,
    80,
    80,
    null,
    'thumbnails_30',
    true
);
```

> These examples write the generated thumbnails in the `thumbnails_30` folder. 
Then we can use these thumbnails in following executions in order to improve speed. 
We can read the thumbnails directory using the utility like this:

```javascript
var mng = require('mosaic-node-generator');

mng.mosaic(
    'input.jpg',
    'pictures',
    30,
    30,
    80,
    80,
    'thumbnails_30',
    null,
    true
);
```

# Tips

- In the first execution, always write the generated thumbnails inside a folder. This is the 8th argument of the `mosaic` function. 
This is useful because it won't exceed the generatio of the mosaic image, as thumbnails will be generated after the mosaic image has been saved.
- In following executions, always read the thumbnails from the thumbnails folder generated in the 1st execution. You will see the speed
increased a lot because what lasts more is the pictures read, specially if pictures are heavy and you have a lot.
- Do not generate a mosaic using too much rows and columns. This will cause the generated image save to fail due to Node.js memory leaks. 
I wouldn't recommend using more than 100-120 rows and columns.
- If you are generating the mosaic using a thumbnails folder, make sure the thumbnails are the same size as the input cell width and height.


