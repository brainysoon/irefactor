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