<template>
  <div class="select">
    <div class="container text-center">
      <h3 class="mb-5">Choose Your Operator!</h3>
      <div class="buttons">
        <button class="btn btn-primary" @click="$emit('changeOperator', '+')">
          Addition (+)
        </button>
        <button class="btn btn-danger" @click="$emit('changeOperator', '-')">
          Substraction (-)
        </button>
        <button class="btn btn-success" @click="$emit('changeOperator', '/')">
          Division (/)
        </button>
        <button class="btn btn-warning" @click="$emit('changeOperator', '*')">
          Multiplication (*)
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
.select {
  margin: 100px auto;
  width: 100%;
}
.container {
  text-align: center;
}
h3 {
  color: #222831;
  font-weight: bold !important;
}
.btn {
  font-size: 23px !important;
  padding: 15px 30px !important;
  letter-spacing: 1px !important;
  transition: 0.3s !important;
  margin: 10px;
}
@media screen and (max-width: 700px) {
  .btn {
    font-size: 1rem !important;
    padding: auto;
  }
}
</style>
