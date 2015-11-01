Example on implementing select2

```javascript
    AccountsTemplates.addField({
      _id: 'languages',
      displayName: 'Choose your language(s)',
      type: 'text',
      template: "languages"
    });
```

client/views/helpers/languages.html

```handlebars
    <template name="languages">
        <div class="at-input">
            <label for="{{_id}}">{{displayName}}</label>
            <input id="at-field-{{_id}}" type="hidden">
            <select id="{{_id}}" class="languages" multiple="multiple" style="width: 100%">
                <option value="Afrikaans">Afrikaans</option>
                <option value="Akan">Akan</option>
            </select>
        </div>
    </template>
```

To be run once after template above is rendered into the dom 
client/views/helpers/languages.js

```javascript
    Template.languages.rendered = function () {
      $(".languages").select2().on("change", function(e) {
        // mostly used event, fired to the original element when the value changes
        $('#at-field-'+e.target.id.substr(2)).val(e.val);
      });
    };
```
