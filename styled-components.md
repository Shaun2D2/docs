# Styled Component Examples

## Basic Example

```
import styled from 'styled-components';

const Button = style.button`
  width: 200px;
  height: 50px;
  background-color: 'red';
`;
```

## Using Props

```
// button.js

import styled from 'styled-components';

const Button = style.button`
  width: 200px;
  height: 50px;
  background-color: ${(props) => props.backgroundColor};
`;

export Button;

// app.js

import { Button } from './button.js';

const App = () => (
  <div>
    <Button backgroundColor="purple"> Click this Button </Button>
  </div>
);

```

## Psudo attributes

```
import styled from 'styled-components';

const Button = style.button`
  width: 200px;
  height: 50px;
  background-color: purple;
  
  &:hover {
    background-color: green;
  }
`;

export Button;
```

## Accessing Child elements

```
import styled from 'styled-components';

const Button = style.button`
  width: 200px;
  height: 50px;
  background-color: purple;
  
  &:label {
    color: white
  }
`;

const ButtonLabel = style.label`
  color: red;
`;

export Button;
```

## Style Reuse in External Component

You can pass a component in directly to add styles from styled component.

```
// button.js
import React from 'react';

const Button = ({ label, className }) => <button className={className}>{label}</button>;

export Button;

// button.styled.js
import style from 'styled-components';

import { Button } from './button.js';

const StyledButton = style(Button)`
  width: 200px;
  height: 50px;
  background-color: purple;  
`;

export StyledButton;

// app.js
import React from 'react';

import StyledButton from './button.styled';

const App = () => (
  <div>
    <StyledButton label="Click here for cheese" />
  </div>
)

```

## Styling Global Components

```
// global.styles.js

import { createGlobalStyle } from 'styled-components';

export const GlobalStyles = createGlobalStyle`
  body {
    margin: 0px;
    padding: 0px;
    background-color: red;
    
`

// app.js
import React from 'react';

import { GlobalStyles } from './global.styles';

const App = () => (
  <div>
    <GlobalStyles />
    <h1>hello world!</h1>
  </div>
);
```
