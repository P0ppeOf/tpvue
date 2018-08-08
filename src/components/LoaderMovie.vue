<template>
<div class = "divCont">
    <div class="loader"></div>
</div>
</template>

<script>
export default {
  name: "Loader"
};
</script>

<style lang="less" scoped>
.loader {

  border: 16px solid #f100e5d2;
  border-radius: 50%;
  border-top: 16px solid #3498db;
  width: 120px;
  height: 120px;
  animation: spin 1s linear infinite;
}
.divCont {
    display : flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    top : 0;
    left: 0;
    height: 100%;
    width: 100%
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
