<template>
  <div class="block__card">
    <label
      >Card Number
      <input type="text" v-model="cardValue" maxlength="16"/>
    </label>
    <div class="block">
      <label class="labelBlock"
        >EXPIRY DATE
        <input type="text" v-model="expiryValue" maxlength="4"/>
      </label>
      <label class="labelBlock"
        >Secure code
        <input type="text" v-model="secureCodeValue" maxlength="3"/>
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: "CreditForm",
  data() {
    return {
        isDisabled: false
    }
  },
  props: {
    cardNumber: {
      type: String,
    },
    expiryNumber: {
      type: String,
    },
    secureCode:{
      type: String,
    }
  },

  computed: {
    cardValue: {
      get() {
        return this.cardNumber;
      },
      set(val) {
        val = val.replace(/\s/g, "");
        val = val.replace(/(\d{4}(?=.+))/g, "$1 ");
        this.$emit("update:cardNumber", val);
      },
    },
    expiryValue: {
      get() {
        return this.expiryNumber;
      },
      set(val) {
        val = val.replace(/(\d{2})(\d{2})/, "$1/$2");
        this.$emit("update:expiryNumber", val);
      },
    },
    secureCodeValue:{
        get(){
            return this.secureCode
        },
        set(val){
            this.$emit('update:secureCode',val)
        }
    }
  },
};
</script>

<style lang="css" scoped>
.block__card {
  width: 30%;
  font-size: 15px;
  padding: 10px 10px;
  display: flex;
  flex-direction: column;
  gap: 20px;
  border: 1px solid black;
}
label {
  text-transform: uppercase;
}
.block {
  display: flex;
  justify-content: space-between;
}
.labelBlock {
  width: 40%;
}
input {
  width: 50%;
}
</style>