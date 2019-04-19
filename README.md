## Getting Started
## Inspired by [service-gen-loader](https://github.com/zhiyingzzhou/service-gen-loader)

**install**

```console
$ npm install service-gen-loader-universal --save-dev
```

**service-mapping.json**

```js
import mapping from './service-mapping.json';
```

Then add the loader to your `webpack` config. For example:

**webpack.config.js**

```js
module.exports = {
    module: {
        rules: [
            {
                test: /-mapping.json$/,
                use: [
                    {
                        loader: 'service-gen-loader',
                        options: {
                            fileName: 'service.js',
                            declareFileName: 'service.d.ts',
                            filePath: (ctx) => {
                                return ctx.context;
                            },
                            declareFilePath: (ctx) => {
                                return path.resolve(ctx.context, '../types');
                            }
                        }
                    }
                ]
            }
        ]
    }
}
```