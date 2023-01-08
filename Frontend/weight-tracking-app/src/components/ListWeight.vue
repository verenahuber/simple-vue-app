<template>
    <div id="ListWeight">
        <span v-show="!isEditable" id="weight" @click="editWeight">{{ entry.weight }}</span>
        <v-text-field 
            id="input" 
            v-show="isEditable" 
            label="Your Weight" 
            v-model="entry.weight" 
            size="100%"
            @focusout="editWeight"
            ref="input">
        </v-text-field>
        <p id="p1">kg</p>
        <span id="p2">{{ entry.date }}</span>
        <button @click="removeWeight">Remove</button>
    </div>
</template>

<script>
export default {
    name: "ListWeight",
    props: ["entry", "index"],
    data: function () {
        return {
            isEditable: false
        };
    },
    methods: {
        removeWeight: function () {
            this.$emit("weightRemoved", {
                index: this.index
            });
        },
        editWeight: function () {
            if (this.isEditable) {
                this.isEditable = false;
                this.$emit("weightEdited", {
                    index: this.index,
                    weight: this.entry.weight
                });
            } else {
                this.isEditable = true;

                // Focus the component, but we have to wait
                // so that it will be showing first.
                this.$nextTick().then(() => {
                    this.focusInput();
                });
            }
        },
        focusInput() {
            this.$refs.input.focus();
        }
    }
};
</script>

<style scoped>
 div {
    display: flex;
  }
  
#ListWeight{
    display: flex;
    flex-direction: row;
    margin-bottom: 20px;
    padding-left: 15px;
    font-size: 20px;
    box-shadow: 0 5px 10px 0 rgba(0, 0, 0, 0.2);
    border-radius: 13px;
    align-items: center;
}
p {
    margin-left: -35px;
    margin-right: 10px;
}

#p2 {
    margin-right: 10px
}

#weight,
#input {
    width: 80px;
    text-align: left;
}

button{
  background-color: #6D60FF;
  border: none;
  color: white;
  padding: 15px 15px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 18px;
  cursor: pointer;
  border-radius: 0 13px 13px 0;
  margin: 0;
}

</style>