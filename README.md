# vue-inputRadio
vue custom radio input, supports object/array options, support multilanguage, support v-model, and support bootstrap 4

## Installation
download/clone and place it to your components directory

## Registering Component

  Locale 
  
     import inputRadio from '~/components/inputRadio.vue'
   
     components: {
       inputRadio
     }

  Global
  
     import inputRadio from '~/components/inputRadio.vue'
     
     Vue.component('inputRadio')
     
 Requirements
 if you need multilanguage supprt you need to create vuex(vue store) file and create getter to get the language
 
     // Default
     vuex : app.js
     getters name : getLanguage()
     
  if you need to change this component default value, then change this following line.
  
    // you can change to your own language getter
    lang: this.$store.getters['app/getLanguage'], 
     
     
 ## Parameter

    v-model : 2 way binding to your model variable (String)
    options : option list (Array or Object)
    name : input name, must unique, used for groups component childs (String)
    input-class : styling class you want to add to the component" (String)
    disabled: set disabled state of component (Boolean)
    
    
## Events

    @input : event fired when user click the radio button
    @changed :event fired when the value is changed
    
    
## Samples
      
  Sample Object  
  
    <inputRadio
      v-model="input1"
      :options="{
        0: {
          id: 'hola',
          eng: 'laho'
        },
        1: {
          id: 'hoiii',
          eng: 'oiiih'
        },
        2: {
          id: 'gggggg',
          eng: 'oiiih'
        }
      }"
      name="objectInput"
      @input="handleInput"
      disabled
    />
    
  Sample Array
  
    <inputRadio
      v-model="fruit"
      :options="['apple','mango','orange']"
      name="inputArray"
    />
  
  
