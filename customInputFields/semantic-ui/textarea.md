This is an example showing how to create a custom input field with a textarea.
It is styled for semantic-ui.

Custom template:

```html
<template name="biographyInput">
  <div class="at-input field">
    <label for="at-field-{{_id}}">
      {{displayName}}
    </label>
    <textarea rows="4" id="at-field-{{_id}}" name="at-field-{{_id}}" {{disabled}}></textarea>
  </div>
</template>
```

UserAccounts configuration:

```javascript
AccountsTemplates.addField({
  _id: 'bio',
  type: 'text',
  displayName: "Short Biography",
  template:"biographyInput"
});
```
