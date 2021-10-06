# React, TypeScript and You :heart:

### Example
// Header.tsx
```
export interface Props {
  title: string,
  color?: string
}

const Header = (props: Props) => {
  const { title, color = 'blue' } = props;
  
  return (
    <header>
      <h1 style={{ color: color }} >{title}</h1>
    </header>
  );
}

```
