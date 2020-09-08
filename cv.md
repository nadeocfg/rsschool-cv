# Frontend Developer

### 1. Name

Alexey Khegay

---

### 2. Contact Info

Email: [khegay.alexey@mail.ru](mailto:khegay.alexey@mail.ru)
Phone: [+7 (705) 577-88-52](tel:+77055778852)
Telegram: [@nadeocfg](https://t.me/nadeocfg)

---

### 3. Skills

- HTML;
- CSS;
- JS;
- SQL
- SASS, LESS;
- Bootstrap;
- Photoshop, Illustrator, Figma;
- Java (base).

---

### 4. Experience

More than 50 projects, since 2013 year.
Latest:

- [https://asterx.kz/](https://asterx.kz/)
- [https://aster.kz/](https://aster.kz/)
- [https://z-star.kz/](https://z-star.kz/)
- [http://steam.z-star.kz/](http://steam.z-star.kz/)
- [http://sauvage.kz/](http://sauvage.kz/)

<details>
 <summary>Code examples</summary>
 <pre>

```javascript
import React, { Component } from "react";
import instance from "../../lib/axios";
import { KEY_API_URL } from "../../lib/env";
import { getChip } from "../../lib/utils";
import { LinearProgress, IconButton, Chip } from "@material-ui/core";
import EditIcon from "@material-ui/icons/Edit";
import ChangeParkNumberDialog from "../ChangeParkNumberDialog";
import moment from "moment";

export default class AllKeys extends Component {
  constructor(props) {
    super(props);

    this.state = {
      assignKeyDialogOpen: false,
      isChangeParkNumberDialogOpen: false,
      currentKey: null,

      //pagintaion
      limit: 10,
      offset: 0,
      allKeys: [],
    };
  }

  getAllKeys = async (limit = 10, offset = 0) => {
    const data = {
      limit: limit,
      offset: offset,
    };

    this.setState({
      isLoading: true,
    });
    let allKeys;
    try {
      allKeys = await instance.post(`${KEY_API_URL}/keys/getKeys`, data).then((response) => response.data.list || []);
      console.log(allKeys);
    } catch (error) {
      console.log({ error });
    }

    this.setState(
      {
        allKeys,
        isLoading: false,
      },
      () => console.log(this.state)
    );
  };

  handleChangeParkNumber = (currentKey) => {
    this.setState(
      {
        currentKey,
      },
      () => {
        this.setState(
          {
            isChangeParkNumberDialogOpen: true,
          },
          console.log(this.state)
        );
      }
    );
  };

  handleChangeParkNumberDialogClose = () => {
    this.setState({
      isChangeParkNumberDialogOpen: false,
    });
    this.getAllKeys();
  };

  componentDidMount() {
    this.getAllKeys();
  }

  render() {
    const { allKeys, isLoading, isChangeParkNumberDialogOpen, currentKey } = this.state;

    if (isLoading) {
      return <LinearProgress />;
    }

    return (
      <div className="keys">
        {allKeys.map((key, index) => (
          <div className="keys__item key" key={index}>
            <div className="key__title">
              <div className="key__title_main">
                <h2>№ {key.keyNumber}</h2>
                {getChip(key)}
                {key.attachDate && <Chip label={moment(key.attachDate).format("DD.MM.YYYY")} color="primary" />}
              </div>

              <h3>
                {key.car.marka.name} {key.car.model.name} {key.car.year}
              </h3>
              <p>{key.car.vin}</p>
            </div>

            <div className="key__stock">
              {key.stockPlace ? (
                <>
                  <p>Сток: {key.stockPlace.stock.name}</p>
                  <p>Ряд: {key.stockPlace.rowNo}</p>
                  <p>Место: {key.stockPlace.placeNo}</p>
                </>
              ) : (
                <p>У машины нет парковочного места</p>
              )}
            </div>

            <div className="key__actions">
              <IconButton color="primary" component="span" onClick={() => this.handleChangeParkNumber(key)}>
                <EditIcon />
              </IconButton>
            </div>
          </div>
        ))}

        <ChangeParkNumberDialog open={isChangeParkNumberDialogOpen} handleClose={this.handleChangeParkNumberDialogClose} currentKey={currentKey} />
      </div>
    );
  }
}
```

 </pre>
</details>

---

### 5. Education

> 2006 - 2010 | Central Asia College of Technology and Economics | Engineer/Programmer

> 2010 - 2013 | Graduate School of Business Almaty Management University | Bachelor's degree of Information Systems and Technologies

---

### 6. English level

Pre-Intermediate (A2)
