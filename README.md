# \<etools-searchable-multiselection-menu\>

Dropdown menu with search and multiple options selection

### Element properties


* autoValidate - boolean
* customObjectOptions - Boolean, Default: false
* disabled - Boolean Default: false
* dynamicAlign - Boolean Default: false
* emptyValue - Boolean Default: false
* errorMessage - string
* falseValue - Boolean Default: false
* hideSearch - Boolean Default: false
* invalid - boolean
* label - String
* menuOpened - Boolean Default: false – notifies
* multi - Boolean Default: false
* noChangeEvent - Boolean, Default: false
* optionLabel - String, Default: label
* options - Array
* optionValue - String, Default: 'value'
* placeholder - string
* required - boolean
* search - String
* selected - Number/Array - notifies
* selectedValues - Object notifies
* showLimitWarning - Boolean
* shownItems - Array
* shownItemsLimit - Number Default: 50
* updateSelected - Boolean, Default: false
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

If you need only select an option and get option ID (most use cases) or an array of IDs(for multiselection) 
you can use `selected` property of the element. It only works for integer values, for other types use `selectedValues` property.
Additionally you can chose to block the change event. Example:

```html
<p>SelectedID: [[selectedId]]</p>
<etools-searchable-multiselection-menu
    label="Searchable menu, custom objects"
    options="[[customObjOptions]]"
    custom-object-options
    option-value="id"
    option-label="option_label"
    selected="{{selectedId}}"
    update-selected no-change-event>
</etools-searchable-multiselection-menu>
```

## Styling

Use this css variables and mixins to style this element.

Custom property | Description | Default
----------------|-------------|----------
`--esmm-option-list-color` | Multiple selected options color | `#212121`
`--esmm-list-item-selected-color` | Selected options bg color | `#DCDCDC`
`--esmm-external-wrapper` | Mixin applied to element wrapper | `{}`


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
