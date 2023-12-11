### To start app `npm run dev`

- Create folder Store - (convention to save the Context in this folder);
- Create XXX-context.js
- there export  import {createContext} from 'react'
        const CartContext = createContext({INITIAL VALUE});

- Providing the context in Component that needs this context.
        - import {XXXX} from './store/xxxx-context';
        - Crate and Export <CartContextProvider>{children} </<CartContextProvider>
            - Wrap it with context;
              <CartContext.Provider value={{items: []}, someHandler: handler}></XXXX.Provider>
              value is REQIURED

- Consuming the context
    - in component we need context import {XXXX} from '../store/xxxx-context';
    - import {useContext} from 'react';
    - Create const cartCtx = useContext(XXXX); To get access to Context
        - Another approach is to use <xxxContex.Consumer> to wrap the component which has to have access to Context
        <CartContext.Consumer>
                  {(cartCtx) => {
                  COMPONENT TO BE RETURNED
                  }}
        </CartContext.Consumer>

    - !!!! if Context is changing the component will reexecuted by React


### useReducer
A function that reduce one or more complex values to a simpler one

- in XXX-context import useReducer
- execute it
  const [shoppingCartState, shoppingCardDispatch] = useReducer();
  useReducer give two cont - first is the state(shoppingCartState) , second - actions(shoppingCardDispatch)
- Outside of the Provider component create new function shoppingCardReducer, which accept two parameters - state and action,
which has to return updated state
- connect reducer Function to usReducer hook.
    - For this pass the pointer to this function shoppingCardReducer, as the first argument to udeReducer
    - Pass the initial state as the second argument
- dispatch Action
    shoppingCardDispatch({
                 type: 'ADD_ITEM',   //type of action
                 payload : id        // payload passed to action
             });
- in shoppingCardReducer describe the action has to be performed
        if(action.type === 'ADD_ITEM'){
             //update sate
         }
- In the component we need data from context
    - import { XXX } from '../store/XXX-context';
     - import { useContext } from 'react';
     - const { items, updateItemQuantity } = useContext(XXX);
