If you wish to integrate UserAccounts and [multiply:iron-router-progress](https://atmospherejs.com/multiply/iron-router-progress)
so to prevent the progress bar to show up on UserAccounts' routes, this is an easy way to achieve it:

```javascript
Router.map(function() {
    this.route('home', {
        path: '/',
    });

    this.route('private');
});

// Protect access to 'private' route
Router.plugin('ensureSignedIn', {
  only: ['private']
});

// Don't show progress bar on 'private' route
Router.routes.private.options.progress = false;


// Don't show progress bars on any UserAccounts route
// ...lets do this at startup-time so the be sure all UA routes
//    are already defined!
Meteor.startup(function(){
  _.each(AccountsTemplates.routes, function(route){
    Router.routes[route.name].options.progress = false;
  });
});
```
