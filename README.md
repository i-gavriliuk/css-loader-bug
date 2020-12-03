# css-loader-bug

## Description

**css-loader** for webpack changes the original css-code formatting

Source code: 'src/main.css' file

```css
@font-face {
  font-family: "Georgia";
  src: url("./assets/fonts/Georgia-Regular.woff2") format("woff2"),   /* double quotes in url() */
       url('./assets/fonts/Georgia-Regular.woff') format("woff");     /* single quotes in url() */
}

.first-div {
  background-image: url("./assets/images/puppy.jpg");                 /* double quotes in url() */
}

.second-div {
  background-image: url('./assets/images/puppy.jpg');                 /* single quotes in url() */
}

.third-div {
  background-image: url(./assets/images/puppy.jpg);                   /* path in url() without quotes */
}
```

Generated code: 'dist/styles/style.css' file

```css

/* all paths in url() without quotes */

@font-face {
  font-family: "Georgia";
  src: url(../fonts/Georgia-Regular.woff2) format("woff2"),
       url(../fonts/Georgia-Regular.woff) format("woff");
}

.first-div {
  background-image: url(../images/puppy.jpg);
}

.second-div {
  background-image: url(../images/puppy.jpg);
}

.third-div {
  background-image: url(../images/puppy.jpg);
}
```

## How Do Reproduce?

- Clone this repo
```bash
git clone https://github.com/i-gavriliuk/css-loader-bug.git
```

- Change dir to the cloned repository
```bash
cd css-loader-bug
```

- Install dependencies
```bash
npm i
```

- Run webpack build
```bash
npm run build
```

- Check css-code
  - Source: '**src/main.css**'
  - Destination: '**dist/styles/style.css**'
