# React Conditionals

In React you can conditionally render components. For example, let's assume we update our products array in `Home.jsx`:

```js
    const initialProducts = [
        { id: 1, name: 'Product 1', price: 10, stock_count: 5 },
        { id: 2, name: 'Product 2', price: 20, stock_count: 5 },
        { id: 3, name: 'Product 3', price: 30, stock_count: 0 },
        { id: 4, name: 'Product 4', price: 40, stock_count: 5 },
        { id: 5, name: 'Product 5', price: 50, stock_count: 5 },
      ];
```

Product 3 now has a `stock_count` of 0, so we want to display an OutOfStockCard component instead.

First, we'll need to change our `ProductList.propTypes` in `ProductList.jsx` to include it:

```jsx
ProductList.propTypes = {
  products: PropTypes.arrayOf(
    PropTypes.shape({
      id: PropTypes.number.isRequired,
      name: PropTypes.string.isRequired,
      price: PropTypes.number.isRequired,
      stock_count: PropTypes.number.isRequired,
    })
  ).isRequired,
};
```

Unsurprisingly, the way we do conditionals in React is pretty much the same as any other language. We're going to use an `if` statement in our `ProductList.jsx` file:

```jsx
    {products.map(product => {
        if (product.stock_count > 0) {
            return (
                <ProductCard key={product.id} product={product}/>
            );
        } else {
            return (
                <OutOfStockCard key={product.id} product={product} />
            );
        }
    })}
```
### OutOfStockCard.jsx

My OutOfStockCard has the same basic structure as my ProductCard, but doesn't need to handle any click events, doesn't have a button to add to cart, and has a different image:

```jsx
import PropTypes from 'prop-types';
import { Card } from 'react-bootstrap';

const OutOfStockCard = ({ product }) => (
    <div className="col-md-4 mb-3">
    <Card style={{ height: '100%' }}>
      <Card.Img variant="top" src={`/outofstock.png`} alt={product.name} />
      <Card.Body>
        <Card.Title>{product.name}</Card.Title>
        <Card.Text>Price: £{product.price}</Card.Text>
        <Card.Text>Stock: {product.stock_count}</Card.Text>
      </Card.Body>
    </Card>
  </div>
);

OutOfStockCard.propTypes = {
    product: 
      PropTypes.shape({
        id: PropTypes.number.isRequired,
        name: PropTypes.string.isRequired,
        price: PropTypes.number.isRequired,
        stock_count: PropTypes.number.isRequired,
      }).isRequired,
  };
  
export default OutOfStockCard;
```