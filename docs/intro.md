# Single Select Component

An accessible Listbox

## Import (Semi-Example)

```jsx
import { useSelect, Select, Option, Options } from "@chakra-ui/react";

const options = {
  defaultValue: ''
  value: ''
  onChange: function(value){
    // state function
  }
};

const { getButtonProps,
        getListboxProps,
        getOptionProps,
        value,
        currentOption,
        listboxVisible,
        setListboxVisible } = useSelect(options);


<Select
   onMouseOver={() => setListboxVisible(true)}
   onMouseOut={() => setListboxVisible(false)}
   onFocus={() => setListboxVisible(true)}
   onBlur={() => setListboxVisible(false)}
>
  <Options {...getListboxProps()}>
    <Option value="" label="" />
  </Options>
</Select>
```

## Research

We have looked at a bunch of existing headed and headless Select components, and our final decisions would be a combination of some of the things that we believe made sense and worked well together.

- Chakra-UI Select
- SaaS-UI Select
- Antd
- use-select
- Downshift
- React Select
- Material UI

## useSelect Hook

The useSelect hook will be able to apply the functionality of an unstyled select components to a different component. This hook will provide the most customization for a select component.

### useSelection options

| Name                       | Required | Type                | Description                                                                                                                                                                                                                                             |
| -------------------------- | -------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `value`                    | true     | any                 | The current value                                                                                                                                                                                                                                       |
| `onChange`                 | -        | Function(value)     | Handler function for when the select option changes. This function can be override to specify own function                                                                                                                                              |
| `shiftAmount`              | -        | Number              | The amount of options to navigate when using the `shift` key. Defaults to 5                                                                                                                                                                             |
| `defaultValue`             | -        | any                 | Initial selected option                                                                                                                                                                                                                                 |
| `defaultOpen`              | -        |                     | Initial open state of dropdown                                                                                                                                                                                                                          |
| `disabled`                 | -        |                     | Whether disabled select                                                                                                                                                                                                                                 |
| `dropdownMatchSelectWidth` | -        | Boolean or Number   | Determine whether the dropdown menu and the select input are the same width. Default set min-width same as input. Will ignore when value less than select width. false will disable virtual scroll                                                      |
| `filterOption`             | -        | Boolean or Function | If true, filter options by input, if function, filter options against it. The function will receive two arguments, inputValue and option, if the function returns true, the option will be included in the filtered set; Otherwise, it will be excluded |
| `filterSort`               | -        |                     | Sort function for search options sorting                                                                                                                                                                                                                |
| `autoFocus`                | -        | Boolean             | If `true`, the select element is focused during the first mount                                                                                                                                                                                         |
| `showArrow`                |          |
| `placeholder`              |          |                     |
| `placement`                |          |                     |
| `isSearchable`             |          | Boolean             | Whether or not the component is searchable                                                                                                                                                                                                              |

## API

| Name              | Type                               | Description |
| ----------------- | ---------------------------------- | ----------- |
| _State_           |                                    |             |
| visibleOptions    | Array(Options)                     | --          |
| selectedOption    | Option                             | --          |
| highlightedOption | Option                             | --          |
| searchValue       | String                             | --          |
| isOpen            | Bool                               | --          |
| _Actions_         |                                    |             |
| highlightIndex    | Function(Int)                      | --          |
| selectOption      | Function(Option)                   | --          |
| removeValue       | Function(Int)                      | --          |
| setOpen           | Function(Bool)                     | --          |
| setSearch         | Function(String)                   | --          |
| _Prop Getters_    |                                    |             |
| getInputProps     | Function(userProps) => inputProps  | --          |
| getOptionProps    | Function(userProps) => optionProps | --          |
| getButtonProps    | Function(userProps) => ButtonProps |             |
| _Other_           |                                    |             |
| optionsRef        | React Ref                          | --          |

## Accessibility

Best practices for accessibility will be applied based on:

- [WAI-ARIA-Practices [combobox]](https://www.w3.org/TR/wai-aria-practices/#combobox)

Also, color theme will apply the appropriate contrast

## Performance

To ensure that the component stays performant, we'll be utilizing React virtualization
