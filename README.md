# \<etools-searchable-multiselection-menu\>

Dropdown menu with search and multiple options selection

### Element properties


* autoValidate - boolean
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
* options - Array
* placeholder - string
* required - boolean
* search - String
* selectedValues - Object notifies
* showLimitWarning - Boolean
* shownItems - Array
* shownItemsLimit - Number Default: 50
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
