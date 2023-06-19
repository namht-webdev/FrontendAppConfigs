# Create React App

```
  npx create-react-app keeptrack --template typescript
```

### .vscode/setting.json

```
    {
    "eslint.validate": [
        "javascript",
        "javascriptreact",
        { "language": "typescript", "autoFix": true },
        { "language": "typescriptreact", "autoFix": true }
    ],
    "editor.formatOnSave": true
    }
```

### eslintrc.json

```
    {
    "extends": ["react-app", "prettier"],
    "plugins": ["prettier"],
    "rules": {
        "prettier/prettier": "error"
    }
    }
```

### prettier

- install

```
    npm install prettier --save-dev
    npm install eslint-config-prettier eslint-plugin-prettier --save-dev
```

- config: .prettierrc

```
    {
    "printWidth": 80,
    "singleQuote": true,
    "semi": true,
    "tabWidth": 2,
    "trailingComma": "all",
    "endOfLine": "auto"
    }
```

### tailwind

- install

```
  npm install -D tailwindcss postcss autoprefixer
  npx tailwindcss init -p
```

- config tailwind.config.js

```
    module.exports = {
    content: ['./src/**/*.{js,jsx,ts,tsx}'],
    theme: {
        extend: {},
    },
    plugins: [],
    };

```

- config index.css

```
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
```

### routing

```
    npm install react-router-dom
    npm install @types/react-router-dom --save-dev
```

### redux, redux toolKit

```
    npm install @types/react-redux
    npm install react-redux
    npm install @reduxjs/toolkit
```

#### Redux configuration

- reducer.ts

```
    import { combineReducers, configureStore } from '@reduxjs/toolkit';
    import { TypedUseSelectorHook, useDispatch, useSelector } from 'react-redux';
    import { ObjectState, objectSlice } from './Slices';

    const rootReducer = combineReducers({
        objects: objectSlice.reducer,
    });
    export const store = configureStore({
        reducer: rootReducer,
    });

    export type RootState = ReturnType<typeof rootReducer>;
    export type AppDispatch = typeof store.dispatch;
    export const useAppDispatch: () => AppDispatch = useDispatch;
    export const useAppSelector: TypedUseSelectorHook<RootState> = useSelector;

    export interface AppState {
    object: ObjectState;
    }
```

### fontAwesome

```
    npm i --save @fortawesome/fontawesome-svg-core
    npm install --save @fortawesome/free-solid-svg-icons
    npm install --save @fortawesome/react-fontawesome
    npm i --save @fortawesome/pro-regular-svg-icons
```

### kiểm tra hiệu suất mạng sử dụng tool WebSurge

```
    https://websurge.west-wind.com/download
```

### Tải xuống module URL Rewrite của IIS để dùng URL của React App trên IIS khi tự nhập link liên kết

```
    https://www.iis.net/downloads/microsoft/url-rewrite.
```

- Tạo file web.config trong thư mục build và thêm

```
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
    <system.webServer>
        <rewrite>
        <rules>
            <rule name="React Router" stopProcessing="true">
            <match url=".*" />
            <conditions logicalGrouping="MatchAll">
                <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
            </conditions>
            <action type="Rewrite" url="/" />
            </rule>
        </rules>
        </rewrite>
    </system.webServer>
    </configuration>
```
