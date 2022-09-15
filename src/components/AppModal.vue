<template>
  <div class="modal-backdrop" @click.self="close">
    <div class="modal">
      <section class="modal-body">
       <h4>Name: {{pokemon.name}}</h4>
       <h4>Height(m): {{pokemon.height_m}}</h4>
       <h4>Classification: {{pokemon.classfication}}</h4>
       <h4>Weight(kg): {{pokemon.weight_kg}}</h4>
        

      </section>
      <button type="button" class="close-button" @click="close">
        Close 
      </button>
    </div>
  </div>
</template>
<script>
export default {
  name: "AppModal",
  props: ['pokemon'],

  methods: {
    close() {
      this.$emit("close");
    },
  },
};
</script>

<style scoped>
.modal-backdrop {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal {
  background: #ffffff;
  box-shadow: 2px 2px 20px 1px;
  overflow-x: auto;
  display: flex;
  flex-direction: column;
  padding: 20px;
  width: 100%;
  max-width: 300px;
}

.modal-body {
  position: relative;
  padding: 20px 10px;
}

.close-button {
  color: white;
  background-color: #082284;
  border: none;
  padding: 10px ;
  cursor: pointer;
  border-radius: 2px;
  transition: all .2s ease;
}

.close-button:hover {
  border: 1px solid #082284;
  background-color: #ffffff;
  color: #082284;
 
}
</style>