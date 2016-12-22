# Angular2 dropdown invalid value directive
### An Angular 2 directive that marks a dropdown as invalid if a specified value is selected.

There are often times that we have a prompt option on a form dropdown, usually labeled "Please select one of the following".

Although this can be an option marked with the `disabled` attribute, which is usually enough to mark an option as a placeholder, if no selection is made, the dropdown box will not be client-side validated.

This directive marks the parent dropdown element as validatable by adding an attribute to that element. The value of the "invalid" option in the dropdown should be the value of the attribute so the directive knows when the dropdown is invalid.

The directive works in conjuction with a databound form. In the example below, if `options` is a collection that is populated by the accompanying component contains a "prompt" option with a value of -1, the ddInvalidValue should be set to -1.

```html
<select [(ngModel)]="selectedOptionValue" id="dropdownbox" name="dropdownbox" 
#dropdownbox="ngModel" ddInvalidValue="-1">
  <option *ngFor="let option of options" [value]="option.id">{{option.text}}</option>
</select>
<div [hidden]="(dropdownbox.valid || dropdownbox.pristine)" class="alert alert-danger">
  Please make a valid selection
</div>
```
