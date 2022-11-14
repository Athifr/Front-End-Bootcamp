# WRITING WEEK 3 FE - DAY 1
## REACT CONTEXT
- Context digunakan ketika beberapa data harus dapat diakses oleh banyak komponen pada tingkat bersarang yang berbeda
- Konsep context sama seperti redux yaitu menghindari props drilling (mengoper props yang sama dari parent ke child-child)
- Redux digunakan untuk project yang benar-benar membutuhkan manage state dan project tersebut termasuk project besar serta kompleks
- Context digunakan untuk project yang tidak terlalu besar dan kompleks
- Context merupakan library eksternal javascript yang digunakan pada react.js
- Dalam context terdapat dua property, yaitu
1. Provider: component untuk tempat menampung value yang didistribusikan kepada `consumer`
```js
    <Provider value={/* some value */}>
```
2. Consumer: component untuk menggunakan data yang disediakan oleh `provider`
```js
    Consumer>
      {value => /* render something based on the context value */}
    </Consumer>
```
- React context biasanya digunakan untuk:
  - Tema (light atau dark mode)
  - User data (authenticated user)
  - Mengatur bahasa (language)
- Dalam menggunakan context tidak perlu menginstall, tinggal mengimport packages yang sudah disediakan folder react


### Menggunakan React Context
- Buat aplikasi react js atau buka folder aplikasi react js jika sudah ada
- Membuat context gunakan `createContext`
```js
  import React, { createContext } from "react";

  const MyContext = createContext(defaultValue);

  export default MyContext;
```

- Menggunakan context
```js
  const componentA = () => {
    return <MyContext.Provider value={'value'}></MyContext.Provider>;
  };
```
- Fungsi `createContext` akan mengembalikan provider dan consumer component

**Tambahan Informasi**
- Alternatif context itu [jotai](https://jotai.org/docs/introduction)
- Jotai membuat semua data bersifat global dengan menggunakan atom



### Menggunakan HOOKS

```useContext``` dapat di katakan sebagai sebuah general store, dengan begitu data dapat kita gunakan di berbagai macam komponen, tanpa harus menjadikan data sebagai props di setiap komponennya, kurang lebih seperti redux, jika teman-teman familiar dengan redux.

```Javascript
import React, { useContext } from "react";
import UserContext from "./UserContext";

const User = () => {
  return (
    <UserContext.Provider value={{ name: "John Doe" }}>
      <div>
        <h1>User</h1>
        <Profile />
      </div>
    </UserContext.Provider>
  );
};

const Profile = () => {
  return (
    <div>
      <h2>Profile</h2>
      <Name />
    </div>
  );
};

const Name = () => {
  const { name } = useContext(UserContext);

  return <p>{name}</p>;
};

export default User;
```

## Day 2
### Membuat Custom Hooks
Custom Hooks dapat dibuat untuk mempermudah penggunaan Context dengan menggunakan ```useContext()```.

```Javascript
import { useContext } from "react";
import UserContext from "./UserContext";

const useUser = () => useContext(UserContext);

export default useUser;
```

Custom Hooks dapat digunakan seperti berikut:

```Javascript
import React from "react";
import useUser from "./useUser";

const User = () => {
  return (
    <UserContext.Provider value={{ name: "John Doe" }}>
      <div>
        <h1>User</h1>
        <Profile />
      </div>
    </UserContext.Provider>
  );
};

const Profile = () => {
  return (
    <div>
      <h2>Profile</h2>
      <Name />
    </div>
  );
};

const Name = () => {
  const { name } = useUser();

  return <p>{name}</p>;
};

export default User;
```
