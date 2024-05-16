# Redux Deep Dive

## Taking a Closer Look

- Handling Async Tasks With Redux
- Where To Put Your Code
- The Redux DevTools

# Steps

## 0. Starting Project

1. add a `README.md` file
2. run `npm install`
3. run `npm start`
4. add a `.gitignore` file & add `node_modules` inside of it

## 1. Refresher / Practice: Part 1/2

1. run `npm install @reduxjs/toolkit`
2. run `npm install react-redux`
3. set up the Redux logic & connect it to the React app
   1. add a `store` folder & inside a `index.js` file to set up the Redux store and so on
   2. create multiple slices: one `cart-slice.js` file for managing the cart & one `ui-slice.js` for the user interface logic
   3. use `createSlice()` to create the different slices & export them as well as their actions
   4. create the store in `store/index.js` with help of `configureStore` & set up the root reducer inside of it & export it
   5. provide the exported store to the application to make effect in the `src/index.js` file with help of the `<Provider>` component
4. in `CartButton.js`, implement the logic to toggle the cart with help of `useDispatch` & the `uiActions`
5. in `App.js`, render the `<Cart>` component conditionally based on the `uiSlice` value that you extract with help of `useSelector`
6. updating the cart items content when we click the `Add to Cart`, the `+` & `-` and the cart badge buttons
   1. create the `cartSlice` with help of `createSlice` in `cart-slice.js`
   2. set up the `cartSlice` logic

## 2. Refresher / Practice: Part 2/2

1. set up the logic for the `removeItemFromCart` function in `cart-slice.js`
2. export the `cartSlice` as default
3. export the `cartActions`
4. in `store/index.js`, merge this `cartSlice` into the overall Redux store
5. wire up the cart actions
   1. add a `DUMMY_PRODUCTS` array in `Products.js` & set the properties based on the properties in `cart-slice.js`
   2. in `ProductItem.js`, wire the `Add to Cart` button to the `addItemToCart` function in `cart-slice.js`
   3. update the cart badge in `CartButton.js` by reading the cart slice `totalQuantity` with help of `useSelector()`
   4. render the cart correctly in `Cart.js` by reading the cart slice `items` with help of `useSelector()`
   5. make the `+` & `-` buttons work in `CartItem.js` with help of `useDispatch()` & `cartActions`
