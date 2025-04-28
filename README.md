# React Native Document Scanner + image cropper 📐🖼

Document in progress...

##### React Native Document Scanner

## Installation 🚀🚀

`$ npm install https://github.com/Jesus-Loroima/react-native-perspective-image-cropper.git --save`

`$ react-native link react-native-perspective-image-cropper`

### metro.config

In you metro.config.js file add the package path for resources react, react native and babel

```
const { getDefaultConfig, mergeConfig } = require('@react-native/metro-config');
const path = require('path');

const defaultConfig = getDefaultConfig(__dirname);

const customConfig = {
    resolver: {
        extraNodeModules: {
            'react': path.resolve(__dirname, 'node_modules/react'),
            'react-native': path.resolve(__dirname, 'node_modules/react-native'),
            '@babel/runtime': path.resolve(__dirname, 'node_modules/@babel/runtime'),
            'react-native-svg': path.resolve(__dirname, 'node_modules/react-native-svg'),
            'react-native-perspective-image-cropper': path.resolve(__dirname, '../react-native-perspective-image-cropper-master'),
        },
        resolveRequest: (context, moduleName, platform) => {
            if (moduleName === 'react-native-perspective-image-cropper') {
                return {
                    filePath: path.resolve(__dirname, '../react-native-perspective-image-cropper-master/index.js'),
                    type: 'sourceFile',
                };
            }

            return context.resolveRequest(context, moduleName, platform);
        },
    },
    watchFolders: [
        ...(defaultConfig.watchFolders || []),
        path.resolve(__dirname, '../react-native-perspective-image-cropper-master')
    ],
};

module.exports = mergeConfig(defaultConfig, customConfig);

```

This library uses react-native-svg and react-native-image-size, you must install them too. See https://github.com/react-native-community/react-native-svg and https://github.com/eXist-FraGGer/react-native-image-size for more infos.

#### Android Only

If you do not already have openCV installed in your project, add this line to your `settings.gradle`

```
include ':openCVLibrary310'
project(':openCVLibrary310').projectDir = new File(rootProject.projectDir,'../node_modules/react-native-perspective-image-cropper/android/openCVLibrary310')
```

## Crop image

- First get component ref

```javascript
<CustomCrop ref={ref => (this.customCrop = ref)} />
```

- Then call :

```javascript
this.customCrop.current.crop();
```
