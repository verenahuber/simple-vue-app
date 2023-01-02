<template>
    <div id="ListWeight">
        <span v-show="!isEditable" id="weight" @click="editWeight">{{ entry.weight }}</span>
        <v-text-field 
            id="input" 
            v-show="isEditable" 
            label="Your Weight" 
            v-model="entry.weight" 
            @focusout="editWeight"
            ref="input">
        </v-text-field>
        <p> kg </p>
        <v-btn @click="removeWeight">Remove</v-btn>
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
    align-items: center;
}

#weight,
#input {
    width: 80px;
    text-align: left;
}

</style>