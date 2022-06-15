
# Vue keyboard accessible modal

The modal is fully customizeable and easy to use.


## Installation

Install the package with npm

```bash
  npm install vue-keyboard-accessible-modal2
```
    
## Usage/Examples
Must have to use `class="keyboard-accessible"` for accessible field
```javascript
<template>
  <div>
    <button aria-label="open" @click="openModal()">Open</button>
    <div>
      <VueKeyboardAccessibleModal2 ref="accessibleModal" :width="modalWidth" :title="modalTitle">
        <input type="text" aria-label="text" class="keyboard-accessible"><br><br>
        <input type="text" aria-label="text" class="keyboard-accessible"><br><br>
        <input type="text" aria-label="text" class="keyboard-accessible"><br><br>
        <button @click="submitData()" aria-label="submit" class="keyboard-accessible">Submit</button>
        <button @click="closeModal()" aria-label="close" class="keyboard-accessible">Close</button>
      </VueKeyboardAccessibleModal2>
    </div>
  </div>
</template>

<script>
import VueKeyboardAccessibleModal2 from 'vue-keyboard-accessible-modal2'

export default {
  components: {
    VueKeyboardAccessibleModal2
  },
  data(){
    return{
      modalTitle: "My modal",
      modalWidth: "50%"
    }
  },
  methods:{
    openModal(){
      this.$refs.accessibleModal.openModal()
    },
    closeModal(){
      this.$refs.accessibleModal.closeModal()
    },
    submitData(){
      alert("Submitted successfully")
    }
  }
}
</script>

```

