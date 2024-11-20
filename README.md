# Base structure for React app

## Installation

```
git clone https://github.com/diominvd/react-app-base
cd react-app-base
npm install
```

## Quick Guide

This repository allows you to quickly deploy a convenient and customized structure for comfortable development of React-based web applications (TypeScript). I believe that TypeScript has an advantage over regular JavaScript, so I use it.

This structure has a comfortable level of nesting, as well as support for aliases for comfortable work with the "zones" of the project.

**The basic structure looks like this:**

```
public/
src/
| app/
| assets/
| config/
| | interfaces/
| | types/
| contexts/
| hooks/
| modules/
| pages/
| providers/
| styles/
| | components/
| ui/
| utils/
```

This structure covers 90% of the needs at the beginning of development. Of course, it can be scaled as needed.

Also, this "base" already includes support for light and dark themes. It is enough to assign a function to switch to onClick. 

**Example of using switchTheme function:**

```
import { useTheme } from '@hooks/useTheme.tsx'

export const Component: React.FC = () => {
  const { switchTheme } = useTheme();
  return (
    <button onClick={ switchTheme }>Click</button>
  )
}
```

It is worth paying attention to the fact that the entire application is wrapped in ThemeProvider, which allows you to call the theme change function at any nesting level of the component.

The colors are configured in a special `src/styles/themes.scss` file. Each parent color must have two child tokens for each mode (light and dark), which will be defined in :root. After that, the parent color is determined twice in the data sectors based on the values of the child tokens. 

**Example of defining colors:**

```
[data-theme='light'] {
  --example-color: var(--example-color-light);
}

[data-theme='dark'] {
  --example-color: var(--example-color-dark);
}

:root {
  /* light theme tokens */
  --example-color-light: white;

  /* dark theme tokens */
  --example-color-dark: black;
}
```

The basic configuration for eslint is also configured in the repository, which allows you to correct errors in a timely manner and keep all code clean.
