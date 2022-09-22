<template>
<!-- <form action="/action_page.php">
  <div class="mb-3 mt-3">
    <label for="email" class="form-label">Email:</label>
    <input type="email" class="form-control" id="email" placeholder="nombre@ejemplo.com" name="user" v-model="user">
  </div>
  <p>Validar Email: <span class="text-success bold">{{email}} </span></p>
  <div class="mb-3">
    <label for="pwd" class="form-label">Password:</label>
    <input type="password" class="form-control" id="pwd" placeholder="Enter password" name="password" v-model="password">
  </div>
  <div class="form-check mb-3">
    <label class="form-check-label">
      <input class="form-check-input" type="checkbox" name="remember"> Remember me
    </label>
  </div>
  <button  class="btn btn-success" @click="submit()">Submit</button>
</form> -->
<div class="form-style">
  <vue-form :state="formState" @submit.prevent="onSubmit">
    <validate tag="label" class="form-style">
      <span>Nombre:</span>
      <input type="text" name="name" id="name" required v-model="data.name">
      <field-messages name="name">
        <div class="text-success">Correcto!</div>
        <div slot="required">Nombre es un campo requerido</div>
      </field-messages>
    </validate>
    <validate tag="label" class="form-style">
      <span>Contraseña:</span>
      <input type="password" name="password" id="password" required v-model="data.password">
      <field-messages name="password">
        <div class="text-success">Correcto!</div>
        <div slot="required">Contraseña es un campo requerido</div>
      </field-messages>
    </validate>
    <button type="submit" class="btn btn-success w-100">Enviar</button>
  </vue-form>
</div>
</template>

<script>
export default {
  data(){
    return{
    formState:{},
    data:{
      name:'',
      password:'',
    }
    }
  },

  methods:{
    onSubmit(){
      if(this.formState.$invalid){
        alert("Error")
        return
      }
      alert("Bienvenido")
    }
  }
}

</script>

<style scoped>
.form-style{
  display:flex;
  flex-direction: column;
  justify-content: center;
  max-width: 500px;
  margin: auto;
}

</style>
