# Styled Components

## Getting Started
```javascript
// <h1> tag with some styles

const Title = styled.h1`
  font-size: 1.5em;
  text-align: center;
  color: palevioletred;
`;

<Title>
  Hello World, this is my first styled component!
</Title>
    
```

*Note:
It is important to define your styled components outside of the render method, otherwise it will be recreated on every single render pass*

## Passed props
`styled-components` pass on all their props.
```javascript
<Input placeholder="@mxstbr" type="text" />
```

###  Dynamic Styles
You can pass a function ("interpolations") to a styled component's template literal to adapt it based on its props.

```javascript
const CustomButton = styled.button`
  color: ${props => props.important ? 'red' : 'black'};
  width: ${props => props.width}px;
}

<CustomButton important={false} width={320}>My button</Button>
`;
```

## Styling any components
The styled method works perfectly on all of your own or any third-party components as well, as long as they pass the className prop to their rendered sub-components.

```javascript
import Link from 'react-router';

const StyledLink = styled(Link)`
  color: palevioletred;
  font-weight: bold;
`;
```

## Extending Styles

```javascript
const Button = styled.button`
  margin: 1em;
  padding: 0.25em 1em;
  border: 2px solid palevioletred;
  border-radius: 3px;
`;

// We're extending Button with some extra styles
const TomatoButton = Button.extend`
  color: tomato;
  border-color: tomato;
`;

render(
  <div>
    <Button>Normal Button</Button>
    <TomatoButton>Tomato Button</TomatoButton>
  </div>
);
```

*Note: You should only use Comp.extend if you know that Comp is a styled component. If you're importing from another file or a third party library, prefer to use styled(Comp) as it accomplishes the same thing but works with any React component*

## Attaching additional props
To avoid unnecessary wrappers that just pass on some props to the rendered component, or element, you can use the .attrs constructor. It allows you to attach additional props (or "attributes") to a component.

```javascript
const Input = styled.input.attrs({
  // we can define static props
  type: 'password',

  // or we can define dynamic ones
  margin: props => props.size || '1em',
})`
  color: palevioletred;
  
  /* here we use the dynamically computed props */
  margin: ${props => props.margin};
`;

render(
  <div>
    <Input placeholder="A small text input" size="1em" />
  </div>
);
```


## Animations

`keyframes` helper will generate a unique name for your keyframes. You can then use that unique name throughout your app.

```javascript
// keyframes returns a unique name based on a hash of the contents of the keyframes
const rotate360 = keyframes`
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
`;

// Here we create a component that will rotate everything we pass in over two seconds
const Rotate = styled.div`
  animation: ${rotate360} 2s linear infinite;
`;

render(
  <Rotate> Something </Rotate>
);
```

## Theming
styled-components has full theming support by exporting a <ThemeProvider> wrapper component. This component provides a theme to all React components underneath itself via the context API. In the render tree all styled-components will have access to the provided theme, even when they are multiple levels deep.

```javascript
// Define our button, but with the use of props.theme this time
const Button = styled.button`
  padding: 0.25em 1em;

  /* Color the border and text with theme.main */
  color: ${props => props.theme.main};
`;

// We're passing a default theme for Buttons that aren't wrapped in the ThemeProvider
Button.defaultProps = {
  theme: {
    main: 'palevioletred'
  }
}

// Define what props.theme will look like
const theme = {
  main: 'mediumseagreen'
};

render(
    <ThemeProvider theme={theme}>
      <Button>Themed</Button>
    </ThemeProvider>
);
```