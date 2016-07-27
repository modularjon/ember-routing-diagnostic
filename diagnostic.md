# Ember Routing Diagnostic

Record your responses inside the fenced code blocks below each question.

1.  What are the main task(s) you perform inside the Ember Application Router,
    and what are the main task(s) you perform inside an Ember Route?

    ```md
    • The Ember Application Router assigns route template names, and optional route path names
    that can differ from the template name. It then dispatches to a route when a
    given url is entered into the browser.

    • An Ember route can describe the model, through route.js, that is used to
    perform data actions, such as calls to a back-end server, and then render the
    data through template.js. It is responsible for delegating data binding, and
    can also describe components.
    ```

1.  What is the command to generate a route named `boston` nested under
    `campus`?

    ```md
    ember g route campus/boston
    ```

1.  Suppose you have a nested route at the URL `/campus/boston`. How would you
    use the `link-to` helper to generate an appropriate link?

    ```md
    {{#link-to 'campus.boston' }}Boston{{/link-to}}
    ```

1.  Explain **at least** two differences between the following two route
    definitions.

    ```js
    this.route('products', function () {
      this.route('product', { path: '/:product_id' }); // <= 👀here
    });

    this.route('product', { path: '/products/:product_id' }); // <= 👀 here
    ```

    ```md
    • The first route definition describes a nested route that would allow access to data from the products route. This is not possible in the second definition.

    • The second route's path description references another route outside of itself. In the first, the nested route's path is just appended to the enclosing route's path.
    ```

1.  Suppose we have the following route definition:

    ```js
    this.route('movie', { path: '/movies/:movie_id' }); // <= 👀 here
    ```

    If we navigate in the browser to `/movies/123`, how can we reference the
    value `'123'` inside a Route?

    ```md
    export default Ember.Route.extend({
      model: function(params) { return params.movie_id; }
    });
    ```

1.  Inside a template, how do we reference data provided by a Route?

    ```md
    By describing model as |<item>|, and then assigning <item>=<item> with the route name preceding the assignment, all in HTMLBars.
     ```
