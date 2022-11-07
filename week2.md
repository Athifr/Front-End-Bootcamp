# WRITING WEEK 2 FE - DAY 1
## REACT JS - Proptypes
PropTypes merupakan library yang dapat membantu dalam memeriksa tipe data props
Contoh:
```js
    import React from 'react';
    import PropTypes from "prop-types";

    const Count = (props) => {
      return (
        <>
          ...
        </>
      )
    };

    Count.propTypes = {
      // put props here
      // key is the name of the prop and value is the PropType
    }
    export default Count;
```

Penggunaan tipe data props pada code
```js
    Count.propTypes = {
      name: PropTypes.string,
      age: PropTypes.number,
      address: PropTypes.object,
    };
```

Penggunaan tipe object pada code
```js
    Count.propTypes = {
      basicObject: PropTypes.object,
      numbers: PropTypes.objectOf(PropTypes.numbers),
      messages: PropTypes.instanceOf(Message),
      contactList: PropTypes.shape({
        name: PropTypes.string,
        phone: PropTypes.string,
      }),
    };
```

# DAY 2
## REACT ROUTER 6
React router merupakan library external yang digunakan untuk routing pada react. Library react router digunakan untuk mengarahkan page satu ke page yang lain berdasarkan path URL yang ditentukan
React router memiliki 2 jenis router yang dapat digunakan, yaitu:
  - <HashRouter>: digunakan jika ingin membuat sebuah web yang static atau tidak ada server untuk me-render data yang dinamis
  - <BrowserRouter>: digunakan jika ingin membuat web yang menggunakan data dinamis dengan server backend

### Varian React Router
React router memiliki beberapa varian berdasarkan platform dan kebutuhan, yaitu:
  - `react-router-dom`: digunakan untuk routing react web
  - `react-router-native`: digunakan untuk routing pada react native
  - `react-router-redux`: digunakan untuk integrasi redux

### Penggunaan React Router
- Import BrowserRouter di file main.jsx `import { BrowserRouter } from ‘react-router-dom’;`
- Buat tag `<BrowserRouter>` di file main.jsx dimana BrowserRouter akan membungkus `<App />`. Semua yang dibungkus oleh BrowserRouter boleh menggunakan fitur react router
```js
  <BrowserRouter>
    <App />
  </BrowserRouter>
```
- File App.jsx:
  - Letakkan `import { Routes, Route, Link } from "react-router-dom";` untuk menampung alamat halaman yang akan dibuat
  - Didalam tag `<Routes>` terdapat tag `<Route />
  - Didalam route terdapat dua properti, yaitu `path` dan `element`
    - `path`: sebagai acuan untuk pindah ke alamat halaman mana 
    - `element`: yang akan memanggil page yang kita punya


## Routing Dasar
Dynamic Routing
Digunakan untuk route pada data yang bersifat dinamis (sering berubah-ubah)
Contoh:
```js
  import {Link,Route, Routes} from 'react-router-dom';
  import Artist from './Artist';
  import './App.css';
  
  function App() {
    return (
      <>
        <ul>
          <li><Link to="/artist/Ariana">Ariana</Link></li>
          <li><Link to="/artist/Taylor">Taylor</Link></li>
        <ul>

        <Routes>
          <Route path="/artist/:name" element={<Artist />}/>
        </Routes>
      </>
     );
  }
```
## Nested Routing
Digunakan bila terdapat banyak rute yang menggunakan parent route yang sama.
Contoh:
```js
  import User from './user/User';
  import Setting from './user/setting/Setting';
  import Profile from './user/profile/Profile';
  import Favorite from './favorite/Favorite';

  function App() {
    return (
      <>
        <ul className='user'>
          <li><Link to="/">Home</Link></li>
          <li><Link to="/user">User</Link></li>
          <li><Link to="/favorite">FavoriteKu</Link></li>
          <li> <Link to="/galeri">Galeri</Link></li>
        </ul>

        <Routes>
          <Route path='/' element={<Home/>}/>
          <Route path='/User' element={<User/>}/>
          <Route path='/Gallery' element={<Gallery/>}/>
          <Route path='/Favorite' element={<Favorite/>}/>

          // Nested router
          <Route path='/Favorite/Music' element={<Music/>}/>
          <Route path='/User/Profile' element={<Profile/>}/>
          <Route path='/User/Settings' element={<Settings/>}/>
        </Routes>
      </>
    );
  }
```
   
