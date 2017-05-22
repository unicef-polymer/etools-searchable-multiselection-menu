# \<etools-searchable-multiselection-menu\>

Dropdown menu with search and multiple options selection

### Element properties
* ajaxParams - Object(optional) used to set build query string for the URL of missing options request.
* allowOutsideScroll - Boolean, default: false
* autoValidate - Boolean
* capitalizeInputShown - Boolean
* customObjectOptions - Boolean, default: false
* disabled - Boolean, default: false
* dynamicAlign - Boolean, default: false
* emptyValue - Boolean, default: false
* errorMessage - string
* falseValue - Boolean, default: false
* hideSearch - Boolean, default: false
* invalid - boolean
* label - String
* menuOpened - Boolean, default: false – notifies
* multi - Boolean, default: false
* noChangeEvent - Boolean, default: false
* noOptionsAvailable - Boolean, default: false
* notFoundValues - Array
* optionLabel - String, default: label
* options - Array
* optionValue - String, default: 'value'
* placeholder - string
* readonly - Boolean, default: false
* required - boolean
* search - String
* selected - Number/Array - notifies
* selectedRequiresValidOptions - Boolean, default: false; using this and selected will ensure selected values will
be set only if the options are not empty
* selectedValues - Object notifies
* showLimitWarning - Boolean
* shownItems - Array
* shownItemsLimit - Number, default: 50
* updateSelected - Boolean, default: false
* url - String, the url used to request selected missing options from server(one missing option `someUrl?values=1`,
many missing options `someUrl?values=1,2,3`). This can be used only with `selected` and `updateSelected` properties.
The response of the missing options request should be an array with one or more objects with the same properties
dropdown options have.
* value - String

## Usage

Examples:

Single selection, with search

```html
<etools-searchable-multiselection-menu
      label="Searchable menu"
      options="[[realOptions]]"
      value="{{selectedValues}}"></etools-searchable-multiselection-menu>
```

Single selection, without search

```html
<etools-searchable-multiselection-menu label="Options menu"
     options="[[realOptions]]"
     value="{{selectedValues}}"
     hide-search></etools-searchable-multiselection-menu>
```

Multi selection, with search

```html
<etools-searchable-multiselection-menu label="Multiselection Searchable menu"
     options="[[realOptions]]"
     value="{{selectedValues}}"
     multi></etools-searchable-multiselection-menu>
```

Single selection, with search, limit of 3 elements

```html
<etools-searchable-multiselection-menu
              label="Searchable menu"
              options="[[realOptions]]"
              shown-items-limit="3"
              value="{{selectedValues}}"></etools-searchable-multiselection-menu>
```

Single selection, with search, always display an empty value (-- None --)

```html
<etools-searchable-multiselection-menu
              label="Searchable menu"
              options="[[realOptions]]"
              empty-value
              value="{{selectedValues}}"></etools-searchable-multiselection-menu>
```

Change event('value-change') examples

```html
<etools-searchable-multiselection-menu
    label="Searchable menu"
    options="[[realOptions]]"
    on-value-change="_singleSelectionChanged"></etools-searchable-multiselection-menu>

<etools-searchable-multiselection-menu
    label="Multi searchable menu"
    options="[[realOptions]]"
    on-value-change="_multiSelectionChanged"
    multi></etools-searchable-multiselection-menu>

```

Error messages and validations. You can use `invalid`, `auto-validate`, `required` to validate your selection.

```html
<etools-searchable-multiselection-menu
        id="dropdownElement"
        label="Searchable menu with validation manually triggered (in 5s)"
        error-message="You must select an option"
        auto-validate required
        options="[[realOptions]]" dynamic-align></etools-searchable-multiselection-menu>

<etools-searchable-multiselection-menu
        id="dropdownElementMulti"
        label="Multi searchable menu with validation manually triggered (in 3s)"
        options="[[realOptions]]"
        placeholder="Select your options"
        error-message="You must select at least an option"
        auto-validate required
        multi></etools-searchable-multiselection-menu>
```

Validation triggered from javascript:

```javascript
this.$.dropdownElement.validate();
// or
this.$.dropdownElementMulti.validate();
```

If the options array where objects of this model: `{value: someIntegerValue, label: someLabel}`
is not what you need you can use any type of objects. You have to set some properties on the element to tell
that you have custom options and which properties to be used as values and labels.
```javascript
// options example(used in the demo), in properties object
customObjOptions: {
    type: Array,
    value: function() {
      var opt = [];
      for(var i = 1; i <= 100; i++) {
        opt.push({
          id: i,
          option_key: 'opt' + i,
          option_label: 'Option ' + i,
          some_other_propery: 'dummy propery for objIdx' + (i -1)
        });
      }
      return opt;
    }
}
```
```html
<etools-searchable-multiselection-menu
        label="Searchable menu, custom objects"
        options="[[customObjOptions]]"
        custom-object-options
        option-value="option_key"
        option-label="option_label"
        on-value-change="_singleSelectionChanged"></etools-searchable-multiselection-menu>
```

If you need only to bind a custom element property to the esmm dropdown use `selected` property
to update dropdown's selection or get selected value(s).
In this case change event is automatically disabled. Example:

```html
<p>SelectedID: [[selectedId]]</p>
<etools-searchable-multiselection-menu
    label="Searchable menu, custom objects"
    options="[[customObjOptions]]"
    custom-object-options
    option-value="id"
    option-label="option_label"
    selected="{{selectedId}}"
    update-selected
    url="http://some-url-to-get-missing-selected-options">
</etools-searchable-multiselection-menu>
```


# \<etools-single-selection-menu\>

Dropdown menu with search and single selection option

### Element properties
* selected - Number/Array - notifies - the id/optionValue of the selected item
* selectedItem - Object - the selected item from the options array
* label - String
* optionLabel - String, default: 'label'
* optionValue - String, default: 'value'
* options - Array - the dataSource of the dropdown
* shownOptions - Array - the displayed options, truncated by shownOptionsLimit
* allowOutsideScroll - Boolean, default: false
* autoValidate - Boolean
* capitalizeInputShown - Boolean
* disabled - Boolean, default: false
* dynamicAlign - Boolean, default: false
* showEmptyValue - Boolean, default: false
* errorMessage - string
* hideSearch - Boolean, default: false
* invalid - boolean
* placeholder - string
* readonly - Boolean, default: false
* required - boolean
* search - String
* shownOptionsLimit - Number, default: 50 - Limit the number of displayed options
* url - String, the url used to request selected missing options from server(one missing option `someUrl?values=1`,
many missing options `someUrl?values=1,2,3`).
The response of the missing options request should be an array with one or more objects with the same properties dropdown options have.
* ajaxParams - Object(optional) used to set build query string for the URL of missing options request.

## Usage

Examples:

Single selection, with search

```html
<etools-single-selection-menu
      label="Searchable menu"
      options="[[realOptions]]"
      selected="{{selectedId}}"></etools-single-selection-menu>
```

Single selection, without search

```html
<etools-single-selection-menu label="Options menu"
     options="[[realOptions]]"
     selected="{{selectedId}}"
     hide-search></etools-single-selection-menu>
```

Single selection, with search, limit of 3 elements

```html
<etools-single-selection-menu
              label="Searchable menu"
              options="[[realOptions]]"
              shown-items-limit="3"
              selected="{{selectedId}}"></etools-single-selection-menu>
```

Single selection, with search, always display an empty value (-- None --)

```html
<etools-single-selection-menu
              label="Searchable menu"
              options="[[realOptions]]"
              show-empty-value
              selected="{{selectedId}}"></etools-single-selection-menu
```

Change event examples:

`on-iron-activate` - fires only when the selected value is changed manually by selecting a value from the dropdown

`on-iron-select` - fires whenever the selected value is changed from dropdown or from code

The event parameter of the method (_singleSelectionChanged) holds info about the item that was selected in: `event.detail.item.item`
```html
<etools-single-selection-menu
    label="Searchable menu"
    options="[[realOptions]]"
    on-iron-activate="_singleSelectionChanged"></etools-single-selection-menu>

<etools-single-selection-menu
    label="Multi searchable menu"
    options="[[realOptions]]"
    on-iron-select="_singleSelectionChanged"></etools-single-selection-menu>

```

Error messages and validations. You can use `invalid`, `auto-validate`, `required` to validate your selection.

```html
<etools-single-selection-menu
        id="dropdownElement"
        label="Searchable menu with validation manually triggered (in 5s)"
        error-message="You must select an option"
        auto-validate required
        options="[[realOptions]]" dynamic-align></etools-single-selection-menu>

```

Validation triggered from javascript:

```javascript
this.$.dropdownElement.validate();
```

If the options array where objects of this model: `{value: someIntegerValue, label: someLabel}`
is not what you need you can use any type of objects. You have to set some properties on the element to tell
that you have custom options and which properties to be used as values and labels.
```javascript
// options example(used in the demo), in properties object
customObjOptions: {
    type: Array,
    value: function() {
      var opt = [];
      for(var i = 1; i <= 100; i++) {
        opt.push({
          id: i,
          option_key: 'opt' + i,
          option_label: 'Option ' + i,
          some_other_propery: 'dummy propery for objIdx' + (i -1)
        });
      }
      return opt;
    }
}
```
```html
<etools-single-selection-menu
        label="Searchable menu, custom objects"
        options="[[customObjOptions]]"
        option-value="option_key"
        option-label="option_label"></etools-single-selection-menu>
```

## Styling

Use this css variables and mixins to style this element.

Custom property | Description | Default
----------------|-------------|----------
`--esmm-option-list-color` | Multiple selected options color | `#212121`
`--esmm-list-item-selected-color` | Selected options bg color | `#DCDCDC`
`--esmm-external-wrapper` | Mixin applied to element wrapper | `{}`
`--esmm-readonly-input-container` | Mixin applied to paper-input-container, readonly | `{}`
`--esmm-readonly-input-container-underline` | Mixin applied to paper-input-container underline, readonly | `{}`
`--esmm-readonly-input-container-label` | Mixin applied to the label in readonly state | `{}`
`--esmm-readonly-input-container-label-focus` | Mixin applied to the label in readonly state with focus | `{}`
`--esmm-list-wrapper` | Mixin applied to list wrapper, can be used to controll list height | `{}`


## Install

```bash
$ bower install --save etools-searchable-multiselection-menu
```

## Preview element locally

Install needed dependencies by running: `$ bower install`.
Make sure you have the [Polymer CLI](https://www.npmjs.com/package/polymer-cli) installed. Then run `$ polymer serve` to serve your element application locally.

## Running Tests

You need to have `web-component-tester` installed (if not run `npm install -g web-component-tester`)
```bash
$ wct
```
or
```bash
$ wct -p
```
