# \<etools-searchable-multiselection-menu\>

Dropdown menu with search and multiple options selection

### Element properties


* falseValue - Boolean Default: false
* hideSearch - Boolean Default: false
* label - String
* menuOpened - Boolean Default: false
* multi - Boolean Default: false
* options - Array
* selectedValues - Object
* value - String - notifies

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
$ wtc
```
or 
```bash
$ wtc -p
```
