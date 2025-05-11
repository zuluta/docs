---
hide:
  #- navigation
  #- toc
---

## **Maquillar el precio de un producto**

En este ejemplo, vamos a maquillar el precio de un producto. Para ello, crearemos una función flecha donde por un lado introduciremos el precio de venta, y por el otro el maquillaje.

```js linenums="1" title="javascript"
const precioMaquillado = (precioVenta, maquillaje) => {
    if (Number.isInteger(maquillaje)) {
        maquillaje = maquillaje * 0.01;
    }
    return `${Math.floor(precioVenta) + maquillaje}€`;
}

const producto_1 = precioMaquillado(4.50, 0.95);
console.log(producto_1); // 4.95€

const producto_2 = precioMaquillado(4.23, 95);
console.log(producto_2); // 4.95€
```

***

<br>
