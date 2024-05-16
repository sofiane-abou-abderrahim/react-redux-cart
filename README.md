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

## 3. Redux & Async Code

1. create a new project in Firebase named `react-redux-cart`
2. keep the link to where you will send your HTTP requests

## 4. Using useEffect with Redux

1. get hold of the overall cart with help of `useSelector()` in `App.js`
2. use `useEffect()` to watch for changes in the cart state
3. inside of it, send a HTTP request to Firebase

## 5. Handling Http States & Feedback with Redux

1. add the new `Notification.js` file inside the `UI` folder
2. use this file to show the notification & handle errors in the `useEffect()` function in `App.js`
3. manage the notification with help of Redux by adding a `notification` property to the `initialState` & a `showNotification` method
4. dispatch the notification when starting sending the data, the data is sent successfully & if there is an error in `App.js`
5. use this new `notification` UI state from `ui-slice.js` with help of `useSelector()` to render the `<Notification>` component conditionally in `App.js`
6. in `App.js`, make sure that you don't send the cart when the app runs for the first time with help of an `isInitial` variable
