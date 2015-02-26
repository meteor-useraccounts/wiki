In case you wish to add a logo above the atForm, this is all you have to do:

1) define a template to include both the logo and the atForm

```html
<template name="myAtForm">
 <div class="ui center aligned three column stackable page grid">
   <div class="at-left eight wide column">
     <h3 class="ui center aligned header">
        <img class="ui small image" src="/imgs/logo.png">
     </h3>
     {{> atForm}}
   </div>
 </div>
</template>
```


2) tell UserAccounts to use your custom template in place of the default one:

```javascript
AccountsTemplates.configureRoute('signIn', {template: myAtForm});
AccountsTemplates.configureRoute('signUp', {template: myAtForm});
```
