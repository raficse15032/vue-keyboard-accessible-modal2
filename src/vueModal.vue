<template>
  <div class="modal-parent modal-close">
    <div :style="{width:width}" class="modal-body">
      <div class="modal-top">
        <span class="heading">{{title}}</span>
        <button @click="closeModal()" aria-label="close" class="modal-close-01">&times;</button>
      </div>
      <div class="modal-form-01">
          <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default /*#__PURE__*/{
  name: 'VueModal',
  props: {
    title: {
      type:String,
      default:'Modal'
    },
    width: {
      type:String,
      default:'80%'
    }
  },
  data(){
    return{

    }
  },

  methods:{
    closeModal(){
      let element = document.querySelector(".modal-parent")
      element.classList.remove('modal-open')
      element.classList.add('modal-close')
    },
    openModal(){
      let element = document.querySelector(".modal-parent")
      element.addEventListener("click", (e) => {
        if(e.target.classList[0] == 'modal-parent'){
          e.target.classList.add('modal-close')
        }
        e.stopPropagation()
      },false)

      element.classList.remove('modal-close')
      element.classList.add('modal-open')
      let elements = document.querySelector('.modal-form-01').getElementsByClassName('keyboard-accessible')
      if(elements.length > 0){
        elements[0].focus()
        elements[0].addEventListener("keydown",(e) => {
          if(e.shiftKey && e.key == 'Tab'){
            e.preventDefault()
          }
        })
        elements[elements.length - 1].addEventListener("keydown",(e) => {
          if(e.key == 'Tab'){
            e.preventDefault()
            document.querySelector('.modal-close-01').focus()
            document.querySelector('.modal-close-01').addEventListener("keydown",(e2) => {
              if(e2.shiftKey && e2.key == 'Tab'){
                e2.preventDefault()
              }
            })
          }
        })
      }
      else{
        document.querySelector('.modal-close-01').addEventListener("keydown",(e2) => {
          if(e2.shiftKey && e2.key == 'Tab'){
            e2.preventDefault()
          }
          else if(e2.key == 'Tab'){
            e2.preventDefault()
          }
        })
      }
    }
  }
}
</script>

<style  scoped>
.modal-parent {
  position: fixed; 
  z-index: 1; 
  padding-top: 100px; 
  left: 0;
  top: 0;
  width: 100%; 
  height: 100%; 
  overflow: auto;
  background-color: rgb(0,0,0); 
  background-color: rgba(0,0,0,0.4); 
}
.modal-open{
  display: block;
}
.modal-close{
  display: none;
}
.modal-parent .modal-body {
  background-color: #fefefe;
  margin: auto;
  padding: 20px;
  border: 1px solid #888;
}
.modal-parent .modal-body .modal-form-01{
  margin-top: 50px;
}
.modal-parent .modal-body .modal-top .modal-close-01 {
  color: #d34fff;
  font-size: 20px;
  font-weight: bold;
  text-decoration: none;
  background: #ffffff;
  padding: 2px 8px;
  border-radius: 40px;
  border: 3px solid #d34fff;
  float: right;
}
.modal-parent .modal-body .modal-top .heading {
  color: #aaaaaa;
  float: left;
  font-size: 28px;
  font-weight: bold;
}

.modal-parent .modal-body .modal-top .modal-close-01:hover,
.modal-parent .modal-body .modal-top .modal-close-01:focus {
  color: #9a0bc9;
  text-decoration: none;
  cursor: pointer;
  transition: 0.5s;
}

</style>
