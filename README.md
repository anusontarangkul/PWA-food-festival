# food-festival

The web app was already created and I helped turned it into a Progressive Web App (PWA).

[screenshot.png](screenshot.png)

|                                         |                                         |                                                   |
| :-------------------------------------: | :-------------------------------------: | :-----------------------------------------------: |
|     [Introduction](#food-festival)      | [Table of Contents](#table-of-contents) | [Development Highlights](#development-highlights) |
|        [Deployment](#deployment)        |    [Page Directory](#page-directory)    |       [Code Hightlights](#code-highlights)        |
| [Technologies Used](#Technologies-Used) |           [Credits](#Credits)           |                [License](#License)                |

## Development Highlights

- Create a downloadable link through creating a manifest.json through webpack-pwa-manifest.
- Used service workers for offline use.
- Bundled files through webpack to minimize files.

## Development

This app was deployed through GitHub pages. You can click the downloadble link in the right side of the URL to download the PWA.

[Deployment](https://anusontarangkul.github.io/food-festival/)

## Page Directory

The build is created through the `dist` folder. The manifest.json is created in the dist and the webpack.config.js is created at the root.

## Code Highlights

Dynamically creating the manifest.json through WebpackPwaManifest plugin.

```JavaScript
        new WebpackPwaManifest({
            name: "Food Event",
            short_name: "Foodies",
            description: "An app that allows you to view upcoming food events.",
            start_url: "../index.html",
            background_color: "#01579b",
            theme_color: "#ffffff",
            fingerprints: false,
            inject: false,
            icons: [{
                src: path.resolve("assets/img/icons/icon-512x512.png"),
                sizes: [96, 128, 192, 256, 384, 512],
                destination: path.join("assets", "icons")
            }]
        })
```

Used the fileloader to add images to the assets folder.

```JavaScript
    module: {
        rules: [
            {
                test: /\.jpg$/i,
                use: [
                    {
                        loader: 'file-loader',
                        options: {
                            name(file) {
                                return "[path][name].[ext]"
                            },
                            publicPath: function (url) {
                                return url.replace('../', '/assets/')
                            }
                        }
                    },
                    {
                        loader: 'image-webpack-loader'
                    }
                ]
            }
        ]
    },
```

## Technologies

- [pwa](https://web.dev/progressive-web-apps/)
- [webpack](https://webpack.js.org/)
- [service-worker](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)

## Credits

The starter code was provided by 2U bootcamp.

|                           |                                                                                                                                                                                                       |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **David Anusontarangkul** | [![Linkedin](https://i.stack.imgur.com/gVE0j.png) LinkedIn](https://www.linkedin.com/in/anusontarangkul/) [![GitHub](https://i.stack.imgur.com/tskMh.png) GitHub](https://github.com/anusontarangkul) |

## License

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/
