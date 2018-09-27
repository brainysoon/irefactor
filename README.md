# irefactor
The collection of refactor methods that we may take when writing code

## Add Parameter
A method needs more information from its caller.
Add a parameter for an object that can pass on this information.

```javascript
const foo = () => {
    console.log('I cannot get the infos from the caller');
}

const bar = (infos) => {
    console.log(`the ${infos} that comes from caller`);
}
```

The short key of this refactor is `cmdF8` and actions name is `change signature` on idea.

## Change Bidirectional Association to Unidirectional
You have a two-way association but one class no longer needs features from the other.

Drop the unneeded end of the association

I thinks this situation is not common in front-end developing.

Like below: `customer` 1 => * `order`

```javascript
const Customer = {
    orders: [...orders]
};

const Order = {
    ...
};
```

## Extract method
You have a code fragment that can be grouped together.

Move this code to a separate new method (or function) and replace the old code with a call to the method.

Like: 
```javascript

const printFoo = () => {
    console.log('print foo');

    console.log('print bar');
    console.log('print bar title');
}

const printBar = () => {
    console.log('print bar');
    console.log('print bar title');
};

const printFooBar = () => {
    console.log('print foo');
    
    printBar();
};

```