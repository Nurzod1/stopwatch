<template>
  <div class="add">
    <svg
      width="20"
      height="20"
      viewBox="0 0 20 20"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <rect x="8.5" width="3" height="20" fill="#9E9E9E" />
      <rect
        y="11.5"
        width="3"
        height="20"
        transform="rotate(-90 0 11.5)"
        fill="#9E9E9E"
      />
    </svg>
  </div>
</template>

<script>
export default {
  name: "AddStopWatch",
};
</script>

<style lang="scss" scoped>
.add {
  width: 225px;
  height: 120px;
  background-color: #696969;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;

  svg {
    rect {
      transition: 0.2s;
    }
  }
  &:hover {
    svg {
      rect {
        fill: #ffffff;
      }
    }
  }
}
</style>