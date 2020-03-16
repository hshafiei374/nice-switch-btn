<template>
  <div class="my-switch-btn">
    <div :class="label_class" :style="label_style">{{label}}</div>
    <input type="checkbox" :id="switch_id" :name="switch_name" v-model="checked" />
    <label :for="switch_id">Toggle</label>
  </div>
</template>

<script>
export default {
  name: "switch-btn",

  props: {
    value: {
      type: [Boolean],
      default: false
    },
    switch_id: {
      type: String,
      default: "my-switch-btn",
      required: true
    },
    switch_name: {
      type: String,
      default: "my-switch-btn"
    },
    label: {
      type: String,
      default: "your label"
    },
    label_class: {
      type: String,
      default: ""
    },
    label_style: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      checked: false
    };
  },
  watch: {
    checked: {
      immediate: true,
      handler() {
        this.$emit("input", this.checked);
      }
    }
  }
};
</script>
<style scoped>
.my-switch-btn input[type="checkbox"] {
  height: 0;
  width: 0;
  visibility: hidden;
}

.my-switch-btn label {
  cursor: pointer;
  text-indent: -9999px;
  width: 67px;
  height: 33px;
  background: grey;
  display: block;
  border-radius: 100px;
  position: relative;
}

.my-switch-btn label:after {
  content: "";
  position: absolute;
  top: 4px;
  left: 5px;
  width: 29px;
  height: 25px;
  background: #fff;
  border-radius: 90px;
  transition: 0.3s;
}

.my-switch-btn input:checked + label {
  background: #bada55;
}

.my-switch-btn input:checked + label:after {
  left: calc(100% - 5px);
  transform: translateX(-100%);
}

.my-switch-btn label:active:after {
  width: 40px;
}
</style>