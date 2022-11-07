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

- **Catatan**:
    - `PropTypes.oneOfType([types])` memberikan pilihan tipe data pada sebuah objek
```js
    Count.propTypes = {
      counts: PropTypes.array,
      users: PropTypes.arrayOf(PropTypes.object),
      alarmColor: PropTypes.oneOf(['red', 'blue']),
      description: PropTypes.oneOfType([
      PropTypes.string,
      PropTypes.instanceOf(Title)
      ]),
      }
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
