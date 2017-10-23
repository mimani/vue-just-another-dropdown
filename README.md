vue-just-another-dropdown
=============

Just another dropdown component, which is intended to be easy to use and bugfree.

## Installation
---------------
### npm
``` sh
npm install --save vue-just-another-dropdown
```

## Usage
---------------

```vue
<script>
import vue from 'vue';
import Dropdown from 'vue-just-another-dropdown';

vue.component('Dropdown', Dropdown);

export default {
  name: 'hello',
  data() {
    return {
      msg: 'Welcome to Just Another Vue.js App',
      cities: ['Bengaluru', 'Delhi', 'Kolkata', 'Bareilly'],
      city: '',
    };
  },
};
</script>

<template>
  <div class="hello">    
    <Dropdown :options="cities" v-model="city" placeholder="City" style="width: 30%"/>
  </div>
</template>
```

## Example
---------------
I have created an [example](https://github.com/mimani/vue-just-another-dropdown/tree/master/example) vue webapp (documentation [here](https://github.com/mimani/vue-just-another-dropdown/blob/master/example/just-another-vue-app/README.md)), demonstrating this dropdown via simple vue webapp, checkout `example` directory in this repo.


## TODOs
---------------
- Add support for multiselect
- Provide options for customised style
- Demo github pages


## Contributions
---------------
All contributions are welcome: use-cases, documentation, code, patches, bug reports, feature requests, etc. You do not need to be a programmer to speak up!
