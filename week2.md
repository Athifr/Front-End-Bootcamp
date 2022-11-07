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
   
# DAY 3
## STATE MANAGEMENT REACT REDUX
Sebuah aplikasi react memiliki beberapa component, jika ingin mengirim data dari component A ke component D, maka harus menambahkan props di component C dan D. Hal ini tidak menjadi masalah jika aplikasi react memiliki sedikit component, tetapi jika component pada aplikasi react bertingkat maka kita harus menambahkan props di setiap component yang dilewati. Hal ini disebut dengan *props drilling*. Props drilling merupakan kegiatan mengoper props yang sama dari parent ke child-child. Salah satu cara mengatasi props drilling adalah dengan menggunakan **Redux** . Redux merupakan salah satu state management. State management adalah library yang digunakan untuk mengelola state pada suatu aplikasi JavaScript.

### Langkah 1: Setup React Redux
- Buat aplikasi react js atau buka folder aplikasi react js jika sudah ada
- Buka terminal aplikasi react dan install redux dengan perintah `npm install redux react-redux`
- Buat folder redux di dalam folder src

### Langkah 2: Setup Redux Store
- Buat file `store.js` pada folder redux

![image](https://user-images.githubusercontent.com/85722923/200301421-161cf241-4157-486e-b74e-2f0a9ae6774c.png)

### Langkah 3: Setup Types
- Contoh kali ini membahas redux yang menyimpan state **counter**
- Buat folder `types` di dalam folder redux dan sebuah file `counter.js`
- Export constanta dengan nama kegiatan tertentu


![image](https://user-images.githubusercontent.com/85722923/200303361-7f390c42-7f5a-4cbc-af8b-4cf6d1879c26.png)

### Langkah 4: Setup Actions
- Buat folder `actions` di dalam folder redux dan sebuah file `counter.js`
- Semua action akan diletakkan pada folder ini


![image](https://user-images.githubusercontent.com/85722923/200303745-192777dd-70ca-4f1f-a533-7d40747e438a.png)
- Penjelasan:
  - Pada line 1 import semua kegiatan yang kita miliki pada tipe kegiatan yang akan terjadi pada reducer counter
  - Pada line 3-5 merupakan sebuah arrow function dengan nama `increment` yang hanya mengirim sebuah object (dispatch) ke reducer kita dengan isian object seperti tertera pada line 4
  - Pada line 7-9 sama dengan baris function sebelumnya hanya beda kegiatan, yaitu `decrement`

### Langkah 5: Setup Reducer
- Buat folder `reducers` di dalam folder redux dan sebuah file pertama `index.js`
- Dalam folder ini semua states akan tinggal
- File index.js digunakan untuk indexing setiap reducer dan menggabungkan semua state yang dimiliki


![image](https://user-images.githubusercontent.com/85722923/200304485-3e08a48d-e81a-4695-8f13-34689ecfe50c.png)
- Penjelasan:
  - Line 1 import `combineReducers` sebuah function dari package redux untuk menggabungkan object-object state yang dimiliki
  - Line 3 import counter dari file Counter.js
  - Line 5 export secara default object yang sudah digabung menggunakan `combineReducers`
- Jika memiliki banyak reducers, maka
```js
  import counter from "./counter";
  import people from "./people";
  import todo from "./todo";

  export default combineReducers({ counter, people, todo });
```
- Buat file reducer dengan nama counter.js pada folder reducers


![image](https://user-images.githubusercontent.com/85722923/200305687-02ae95f3-bead-4d88-9c5a-da71ac684701.png)
- Penjelasan:
  - Pada line 1 sama seperti pada file actions/counter.js dimana kita import semua kegiatan yang akan terjadi pada reducer counter
  - Pada line 3 buat sebuah variable dengan nama `initialState` yang mana isinya adalah sebuah object untuk menampung keadaan state dari reducer counter pada saat aplikasi pertama kali di load
  - Pada line 7 buat function reducer, dimana function ini menerima argument state yang akan diisi dengan `initialState` ketika pertama diload dan argument kedua yaitu `action`, argument action ini akan berisi sesuai dengan object yang dikirim dari file [/src/redux/actions/counter.js], yaitu `{ type: INCREMENT }`
  - Pada line 8-15 buat logic pemisah setiap kegiatan dengan code `switch` dan dicek berdasarkan `action.type`
  - Pada line 9-10 deklarasikan setiap kegiatan, kita bisa taruh logic penyimpanan state kita pada baris tersebut seperti melakukan mapping data, memfilter data, data penjumlahan dan lainnya
  - Pada line berikutnya kita bisa sisipkan kegiatan yang lain
  - Pada line 18 `export default reducer` agar bisa digunakan pada file [/src/redux/reducers/index.js]

### Langkah 6: Provider
![image](https://user-images.githubusercontent.com/85722923/200307859-bd7c5af1-39de-4e74-83c9-51c7cb8bdedf.png)
- Penjelasan:
  - Pada line 7-8 import Provider dari react-redux dan store data pada folder [redux/store/index.js]
  - Pada line 12-14 bungkus aplikasi dengan Provider dan sertakan props store yang diisi store

### Langkah 7: App.js
![image](https://user-images.githubusercontent.com/85722923/200308644-9aeb9975-5f28-4b3c-ae20-f2291aeb4687.png)
- Penjelasan:
  - Pada line 3 import `useSelector` dan `useDispatch` dari react-redux
  - Import setiap kegiatan yang dibutuhkan pada line 5 yaitu increment dan decrement dari file [/src/redux/actions/counter.js]
  - Pada line 8 buat variable baru dengan nama `counter`, lalu isi dengan cara panggil function `useSelector` dan sisipkan arrow function
  - Function callback tersebut menerima 1 argument yaitu `state` lalu pada bagian returnnya panggil `state.counter` atau `state[namaReducer]` jika memiliki reducer lainnya
  - Pada line 9 siapkan function `dispatch` untuk melakukan action nantinya
  - Pada line 15-17 terdapat dua button untuk menambah atau mengurangi state saat ini dan 1 text untuk menunjukkan keadaan state saat ini
  - Pada setiap function beri event `onClick` dimana ketika diclick button akan menjalankan sebuah function dispatch dan sisipkan action yang sudah dibuat sebelumnya pada file [/src/redux/actions/counter.js]
    
# Day 4
    
## To do list
Making to do list

# Day 5

## Redux Thunk

Menambahkan redux thunk
```
npm install redux-thunk@2.3.0
```
