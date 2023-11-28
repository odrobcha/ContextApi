- Create folder Store - (convention to save the Context in this folder);
- Create XXX-context.js
- there export  import {createContext} from 'react'
        const CartContext = createContext({INITIAL VALUE});

- Providing the context in Component that needs this context.
        - import {XXXX} from './store/xxxx-context';
        - Crate and Export <CartContextProvider>{children} </<CartContextProvider>
            - Wrap it with context;
              <CartContext.Provider value={{items: []}, someHandler: hadler}></XXXX.Provider>
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



