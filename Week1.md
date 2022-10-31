#  DAY 1
## INTRODUCTION REACT JS
### Apa itu React JS
React adalah library JavaScript yang deklaratif, efisien, dan fleksibel untuk membangun antarmuka pengguna. React memungkinkan Anda untuk membuat antarmuka kompleks dari kumpulan kode yang kecil dan terisolasi yang disebut “komponen”. Sistem yang membantu javascript dapat berjalan diluar browser adalah Node.js
  - Node.js dibagian front-end hanya sebatas untuk menginstall react
  - File ekstensi dari javascript pada react adalah jsx

### Instalasi React JS
- Install [Node.js](https://nodejs.org/en/download/) versi LTS
- Buka terminal (git bash) ketikkan `npx create-react-app nama_aplikasi`
- Ketikkan `y` dan enter
- Tunggu proses loading sampai git bash menampilkan “Happy hacking!”
- Buka folder aplikasi di visual studio code

### Struktur Folder React JS
- Terdapat tiga folder dalam folder aplikasi react (node_module, public, src)
- Folder node_modules merupakan packages-packages yang digunakan untuk project react. Tetapi folder ini diabaikan saja
- Folder public berisi struktur web utama, seperti satu file .html, logo, dan lainnya
- Didalam file .html terdapat `div id=”root”` yang nantinya disisipkan halaman home, about, contact, dan lainnya. Pada file inilah metode SPA
- Folder public juga diabaikan
- Folder src akan dikotak-katik. Folder ini memiliki file utama yaitu index.js
- Didalam index.js akan mengimport react dan membuat sebuah virtual DOM, dimana nantinya akan mengambil element id=”root” `getElementById(‘root’)` pada file .html di folder public
- Setelah itu root akan merender atau menampilkan function dengan return value html
- Untuk menjalankan folder react buka terminal (bash), ketikkan `cd nama_aplikasi` dan `npm start`

## FITUR VIRTUAL DOM
Virtual DOM (VDOM) adalah sebuah konsep dalam pemrograman di mana representasi ideal atau “virtual” dari antarmuka pengguna disimpan dalam memori dan disinkronkan dengan DOM “yang sebenarnya” oleh library seperti ReactDOM. Proses ini disebut reconciliation.
- Cara kerja virtual DOM:
  - Virtual DOM menyalin semua node yang ada pada DOM kedalam bentuk JSON
  - React mengubah state aplikasi
  - Virtual DOM baru dibuat oleh react berdasarkan Virtual DOM lama, namun dengan mengikuti perubahan state (Virtual DOM lama tetap ada)
  - Virtual DOM lama dan Virtual DOM baru dibandingkan untuk mengetahui letak node yang berubah
  - Setelah mengetahui node mana yang berubah, maka Virtual DOM baru menyalin node yang berubah ke DOM

## JSX (*JavaScript Syntax Extension*)
Menulis JSX hampir sama dengan menulis HTML. Anda dapat menggunakan tag yang benar-benar sama seperti HTML, seperti h> dan h2 untuk judul atau p untuk paragraf, dan div untuk kolom dan container. Meskipun JSX sangat mirip dengan HTML, ada beberapa perbedaan. Seperti yang ditunjukkan di gambar sebelah kiri, beberapa element tidak dapat diletakkan di dalam return. Jika Anda memiliki lebih dari satu element, gabungkan element-element tersebut ke dalam satu tag div seperti contoh di sebelah kanan.
  
- JSX adalah ekstensi react untuk javasript
- JSX terlebih dahulu akan dicompile menjadi javascript sebelum ditampilkan pada browser
- JSX digunakan untuk menulis HTML pada file ekstensi javascript


Day 2
# DAY 2
## Membuat Folder React
Terdapat 2 cara untuk membuat folder react:
Cara 1
  - Buka terminal (bash) ketikkan `npx create-react-app nama_aplikasi`
  - Tunggu proses loading sampai git bash menampilkan “Happy hacking!”
  - Ketikkan `cd nama_aplikasi`
  - Perintah untuk menjalankan project `npm start`
Cara 2
  - Buka terminal (bash) ketikkan `npm create vite@latest nama_aplikasi --template react`
  - Ketikkan `y` dan enter
  - Pilih framework `react`
  - Pilih variant `javascript`
  - Ikuti perintah yang sudah tertera di terminal:
    - `cd nama_aplikasi`
    - `npm install`
    - `npm run dev` perintah untuk menjalankan project
    - Buka link local di terminal dengan `ctrl + click link`
Perbedaan kedua cara membuat folder react ini hanya pada kecepatan loading install dan struktur folder, dimana pada vite beberapa file akan dihapus tetapi tidak mempengaruhi project. Jika menggunakan vite maka file utama di folder src memiliki ekstensi .jsx (main.jsx) yang sebelumnya .js

## REACT JS COMPONENT
Secara konsep, komponen mirip dengan fungsi pada Javascript. Komponen menerima beberapa masukan (biasa disebut “props”) dan mengembalikan element React yang mendeskripsikan apa yang seharusnya tampil pada layar.
Cara paling sederhana untuk mendefinisikan sebuah komponen adalah dengan menuliskan sebuah fungsi Javascript:
```
  function Welcome(props) {
  return <h1>Halo, {props.name}</h1>;
}
```
Fungsi ini adalah komponen React yang sah karena menerima sebuah “props” tunggal (yang bertindak sebagai props) atau argumen objek dengan data dan kembalian sebuah elemen React. Kita menyebut komponen karena itu benar-benar merupakan fungsi Javascript
- Terdapat dua cara membuat component
  - Gunakan class
  ```js
      import React, {Component} from 'react'

      export default class Header extends Component {
        render() {
          return (
            <h1>Judul Halaman</h1>
          )
        }
      }
  ```
      
  - Gunakan function (rekomendasi dari dokumentasi resmi react js)
  ```js
      const NamaComponent = () => {
        return (
          <div>
            <h1>Ini contoh component</h1>
          </div>
        )
      }

      export default NamaComponent
  ```
- Cara membuat react js component
  - Buat folder `components` di dalam folder src
  - Sesuaikan nama file atau folder dengan component yang akan dibuat. Misal mau membuat member buat nama filenya `MemberInfo.jsx`
  - Nama folder, file, dan function component harus menggunakan huruf kapital diawal dan di kata selanjutnya
  - Panggil component pada halaman yang membutuhkan dengan import component pada file App.js
  
## PROPS DAN STATE
  ### Props
Props merupakan argumen yang di-passing dari satu komponen ke komponen lain. Cara passing props sangatlah mudah, yaitu dengan menulisnya sebagai atribut pada elemen HTML. Props digunakan untuk melakukan komunikasi data antara komponen parent dan child. Berikut contoh props.
  ```
  import React from 'react';
 
function Parent() {
  return <Child name="Nusantech Academy" />
}
 
function Child(props){
  return (
    <div>
      <h1>Hello {props.name}</h1>
    </div>
  )
}
 
export default Parent;
  ```
### State
State merupakan tipe data pada komponen React yang bersifat privat. Artinya, data dengan tipe state hanya dapat digunakan di dalam komponen itu sendiri. Komponen yang di dalamnya terdapat state disebut stateful component. Sebaliknya, komponen yang di dalamnya tidak menggunakan state disebut stateless component. State menyimpan nilai properti dari suatu komponen. Jika state berubah maka komponen akan dirender ulang. Berikut contoh state.
- Cara menggunakan state:
  ```
  import React from 'react'
 
class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {name: "Nusantech Academy"};
  }
  render() {
    return (
      <div>
        <h1>Hello {this.state.name}</h1>
      </div>
    );
  }
}
 
export default App
  ```
  - Mengakses nilai state dengan curly brackets `{}`
  ```js
      import React, { useState } from 'react'; // import useState

      export default function App() {
        const [state, setState] = useState('brachio');

        return (
          <div>
            <h1>Hello Devsaurus</h1>
            <p>My Name is {state}</p>
          </div>
        );
      }
  ```
  - Mengupdate data state dengan `setState()`
  ```js
      import React, { useState } from 'react';

      export default function App() {
        const [state, setState] = useState('brachio');

        const handleChange = () => {
          setState('t-rex');
        };

        return (
          <div>
            <h1>Hello Devsaurus</h1>
            <p>My Name is {state}</p>
            <button onClick={handleChange}>Change Name</button>
          </div>
        );
      }
  ```

## REACT JS STYLING
Terdapat beberapa cara melakukan styling pada component react js
External CSS
  - Cara ini sama seperti membuat external CSS biasa
  - Buat file .css lalu import filenya ke component yang dibuat
  - Styling yang ada pada file css akan di implementasikan pada component sesuai `className` yang dipanggil
  ```css
      .DottedBox {
        margin: 40px;
        border: 5px dotted pink;
      }

      .DottedBox_content {
        font-size: 15px;
        text-align: center;
      }
  ```
  ```js
      import React from 'react'
      import './DottedBox.css'

      const DottedBox = () => (
        <div className="DottedBox">
          <p className="DottedBox_content">Get started with CSS styling</p>
        </div>
      )

      export default DottedBox
  ```


Day 3
#  DAY 3
## REACT JS EVENTHANDLER
- React dapat menghandle sebuah event yang memiliki perbedaan dengan handling event pada DOM element
- React event menggunakan camelCase, bukan lowercase
- Handler untuk event adalah sebuah function yang ditulis diantara curly braces `{}` dan tidak ditulis dalam bentuk string. Contoh
```js
    import React, { useState } from 'react';

    export default function App() {
      const [state, setState] = useState('brachio');

      const handleChange = () => {
        setState('t-rex');
      };

      return (
        <div>
          <h1>Hello Devsaurus</h1>
          <p>My Name is {state}</p>
          // event react menggunakan {}
          <button onClick={handleChange}>Change Name</button>
        </div>
      );
    }
```
- Penjelasan:
  - Event klik button pada react tidak ditulis onclick tapi **onClick**
  - Event `handleChange` untuk menghandle event onClick
  - Ketika button diklik maka function handleChange akan dieksekusi

### Event Handler dengan Argument
- Event handler dengan argument harus ditulis dengan menggunakan arrow function
- Jika ditulis tanpa arrow function maka event handler tidak dieksekusi sesuai dengan event yang terjadi dalam component
```js
    import React, { useState } from 'react';

    export default function App() {
      const [state, setState] = useState('brachio');

      const handleChange = (name) => {
        setState(name);
      };

      return (
        <div>
          <h1>Hello Devsaurus</h1>
          <p>My Name is {state}</p>
          //event handler ditulis dengan arrow function
          <button onClick={() => handleChange('t-rex')}>Change Name</button>
        </div>
      );
    }
```
