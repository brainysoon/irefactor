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

## Inline Method
When a method body is more obvious than the method itself, use this technique.

Replace calls to the method with the method's content and delete the method itself.

In Js it's more liek:

```javascript

const foo = () => {
    formatToYYYYMMDD(time);
};

const formatToYYYYMMDD() = (time) => {
    time.format('yyyy-mm-dd');
};

const bar = () => {
    time.format('yyyy-mm-dd');
};

```

## Extract Variable
You have an expression that is hard to understand.

Place the result of the expression or its parts in separate variables that are self-explanatory.

I think this is very useful if the expression is too long to understand

Like: 
```javascript
const foo = isWithinChina() && theCity === 'Chengdu' && theCompany === 'ThoughtWorks' || theName === 'TWer';

const isWithinChengduOffice = isWithinChina() && theCity === 'Chengdu' && theCompany === 'ThoughtWorks';
const isTWer = theName === 'TWer'; 

const foo = isWithinChengduOffice && isTWer;
```