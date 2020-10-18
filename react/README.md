# React

- Do not use React with TypeScript
- Use [children-style] routes when using [React Router]
- Prefer [Function Components] over [Class Components]
- Use `PascalCase` for component names and their file names
- Use [React Hooks]
- Use pre-built hooks when possible (e.g. [streamich/react-use])
- Avoid [Higher-Order Components] and [recompose] (see hooks above as an
  alternative)
- Do not use PropTypes or defaultProps.
- Prefer the [short syntax] when using [Fragments]
- Prefer [React Contexts] over [Redux]
- Avoid using indexes as the value for [keys]
- Prefer [component composition over component inheritance]
- Prefer [CSS-in-JS] over stylesheets

## General Philosophies

### CSS-in-JS

- No HTML tags in the main render function of components
- Use system components, with inline styles for variants

  - For single line styles, you can write directly in the `style` prop. eg. `<Body style={{ marginBottom: theme.spacing['0'] }} />`
  - Use a style object for multi-line styles. eg.

    ```js
      const styles = {
        body: {
          marginBottom: theme.spacing['0'],
          paddingBottom: theme.spacing['4'],
        },
      }

      <Body style={styles.body} />
    ```

- No magic values in styles, use values from the theme specification in `shared/theme.js` for variants instead
- Only use [styled-components] for pseudo-classes, eg. `a:hover`
- If a component is re-used across a lot of other components, feel free to propose a new system component. It is an evolving set of components to speed up the process of development.
- Refactor existing inline HTML tags to the appropriate system component if you make changes to the UI.

#### The future

We are aiming towards introducing [React Native Web] as our CSS-in-JS framework. The belief here is that we can share similar components across web and mobile.

This isn't our current reality though. Rather than introduce an alternative that we migrate away from, we have decided to write inline styles. This is the easiest to understand and doesn't require learning another library. It should be easy to convert into RNW in the future.

### Testing

- Use [testing library] for all new components
- Create test cases to cover all states for a component
- Don't mock child components but do mock API requests with [Jest]
- The setup for a test should look as close to how you intend to use it as possible. eg. A route should be wrapped in a `Router`.
- Add the minimum number of capybara specs to drive integration of the full stack.

[testing library]: https://testing-library.com/docs/react-testing-library/intro
[jest]: https://jestjs.io
[styled-components]: https://styled-components.com/
[css-in-js]: https://speakerdeck.com/vjeux/react-css-in-js
[children-style]: https://docs.google.com/document/d/15KCY5PP65vnGWUhu5qAPwlPhgrl26AjIWZywlW4zu5k/edit
[react hooks]: https://reactjs.org/docs/hooks-overview.html
[custom hooks]: https://reactjs.org/docs/hooks-overview.html#building-your-own-hooks
[streamich/react-use]: https://github.com/streamich/react-use
[function components]: https://reactjs.org/docs/components-and-props.html
[class components]: https://reactjs.org/docs/react-component.html
[forward refs]: https://reactjs.org/docs/forwarding-refs.html
[higher-order components]: https://reactjs.org/docs/higher-order-components.html
[recompose]: https://github.com/acdlite/recompose
[render props]: https://reactjs.org/docs/render-props.html
[typescript prop interfaces]: https://www.typescriptlang.org/docs/handbook/react-&-webpack.html#write-some-code
[proptypes]: https://reactjs.org/docs/typechecking-with-proptypes.html
[short syntax]: https://reactjs.org/docs/fragments.html#short-syntax
[fragments]: https://reactjs.org/docs/fragments.html
[react contexts]: https://reactjs.org/docs/context.html
[redux]: https://react-redux.js.org/
[keys]: https://reactjs.org/docs/lists-and-keys.html#keys
[component composition over component inheritance]: https://reactjs.org/docs/composition-vs-inheritance.html
[react router]: https://reacttraining.com/react-router/
[react native web]: https://github.com/necolas/react-native-web
