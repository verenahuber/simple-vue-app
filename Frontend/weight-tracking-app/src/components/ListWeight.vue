<template>
    <div id="ListWeight">
        <v-text-field 
            id="input"   
            v-model="entry.weight" 
            @focusout="editWeight"
            variant="plain"
            suffix="kg">
        </v-text-field>
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
            this.$emit("weightEdited", {
                    index: this.index,
                    weight: this.entry.weight
                });
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
    box-shadow: 0 3px 5px 1px rgba(0, 0, 0, 0.2);
    border-radius: 13px;
    align-items: center;
}
p {
    margin-left: -55px;
    margin-right: 20px;
}

#p2 {
    margin-right: 47.5px;
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
  padding: 13px 15px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 18px;
  cursor: pointer;
  border-radius: 0 13px 13px 0;
  margin: 0;
}

</style>