wiki
====

Official WIki Pages for UserAccounts

#useraccounts:bootstrap

##Modal singin/signup forms

#### First add this excellent modal package to your Meteor project
[peppelg:bootstrap-3-modal package](https://atmospherejs.com/peppelg/bootstrap-3-modal)

#### Next create a signin template and _add these modal classes_
```
<template name="login">
  <div class="modal fade">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-body">
        <div id="login" class="form-signin">
            {{> atForm}}
        </div>
        </div>
      </div>
    </div>
  </div>
</template>
```
#### To show your modal call Modal.show from your event handler 
```
Modal.show('login'); // login being the template name
```

example:
```
Template.header.events({
  'click .__signin': function() {
    Modal.show('login');
  },
});
```
#### To hide the modal, add this onSubmitHook to your AccountsTemplate config
```
AccountsTemplates.configure({
    onSubmitHook: mySubmitFunc
});
```
#### then write a callback to hide your signin/signup form
```
var mySubmitFunc = function(error, state){
  if (!error) {
    if (state === "signIn") {
      // Successfully logged in
      // ...
      Modal.hide('login');
    }
    if (state === "signUp") {
      // Successfully registered
      // ...
      Modal.hide('login');
    }
  }
};
```

[Look Ma! Modal sign-in!](http://screencast.com/t/TURoOpAU)

#### Modal header/footer
If you want to show the form title in the modal-header section, be sure to set the signin title to empty string in AccountsTemplate.config otherwise {{atForm}} will produce a default title in the modal-body block

```
  title: {
      forgotPwd: "Recover Your Password",
      signIn: "",
```
then you can just show it yourself in the header
```<div class="modal-header>Sign-in</div>```


