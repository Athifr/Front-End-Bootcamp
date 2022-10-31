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
cara membuat component

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
Cara menggunakan state:
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

Mengupdate data state dengan `setState()`
  ```
  js
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
React dapat menghandle sebuah event yang memiliki perbedaan dengan handling event pada DOM element. Handler untuk event adalah sebuah function yang ditulis diantara curly braces `{}` dan tidak ditulis dalam bentuk string. Contoh
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


### Event Handler dengan Argument
Event handler dengan argument harus ditulis dengan menggunakan arrow function tanpa arrow function maka event handler tidak dieksekusi sesuai dengan event yang terjadi dalam component.
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
# Day 4
## Hooks 
Hooks merupakan fitur baru di React 16.8. Dengan Hooks, kita dapat menggunakan state dan fitur React yang lain tanpa perlu menulis sebuah kelas baru. Hooks membuat Anda mampu untuk memecah satu komponen besar menjadi beberapa fungsi kecil yang berisi bagian-bagian yang saling berhubungan (seperti pemasangan langganan atau pengambilan data), daripada memaksa dengan memecah bagian per bagian di lifecycle method yang ada. Anda juga dapat melakukan pengelolaan local state komponen dengan reducer untuk membuatnya lebih mudah diprediksi.

Menggunakan Hooks:
Effect Hook memungkinkan Anda melakukan efek samping (side effects) didalam function component:
```
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  // Mirip dengan componentDidMount dan componentDidUpdate:
  useEffect(() => {
    // Memperbarui judul dokumen menggunakan API browser
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

# Day 5

## Form pada React 
Elemen form HTML bekerja sedikit berbeda dari elemen DOM lainnya di React, karena elemen form secara natural menyimpan beberapa state internal. Sebagai contoh, form ini pada HTML biasa menerima nama tunggal:
```
<form>
  <label>
    Name:
    <input type="text" name="name" />
  </label>
  <input type="submit" value="Submit" />
</form>
```
Jika Anda menginginkan perilaku seperti ini di React, ini sebenarnya dapat bekerja. Namun di banyak kasus, akan lebih mudah untuk memiliki sebuah fungsi JavaScript yang menangani sebuah submisi dari sebuah form dan memiliki akses terhadap data yang dimasukkan pengguna ke dalam form. Cara standar untuk mencapai hal ini adalah dengan teknik yang disebut ”controlled component“.

### Controlled Component
Pada HTML, elemen form seperti <input>, <textarea>, dan <select> biasanya menyimpan state mereka sendiri dan memperbaruinya berdasarkan masukan dari pengguna. Di React, state yang dapat berubah seperti ini biasanya disimpan pada properti dari komponen, dan hanya akan diubah menggunakan setState().

Kita dapat menggabungkan keduanya dengan menggunakan state pada React sebagai “sumber kebenaran satu-satunya”. Kemudian komponen React yang me-render sebuah form juga mengontrol apa yang terjadi dalam form tersebut pada masukan pengguna selanjutnya. Sebuah elemen masukan form yang nilainya dikontrol oleh React melalui cara seperti ini disebut sebagai ”controlled component“.
  
Contoh:
  ```
  class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
  ```
