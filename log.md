```typescript
// axios example
// baseURL = 백엔드주소

export const instance = axios.create({
  baseURL,
  headers: {
    user: JSON.stringify(getLsUser()),
    loggedin: JSON.stringify(getLsLoggedIn()),
    // headers의 이름들은 소문자만 가능

    'Content-Type': 'multipart/form-data',
  },
});

instance.interceptors.request.use(
  (config: AxiosRequestConfig<any>) => {
    config.headers = {
      ...config.headers,
      user: JSON.stringify(getLsUser()),
      loggedin: JSON.stringify(getLsLoggedIn()),
      // headers의 이름들은 소문자만 가능

      'Content-Type': 'multipart/form-data',
    };

    return config;
  },
  (error: any) => {
    console.log(error);
    return error;
  }
);
```
