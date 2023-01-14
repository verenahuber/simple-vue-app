<template>
    <div class="container" id="ListWeight">
        <v-text-field  
            v-model="entry.weight" 
            @focusout="editWeight"
            class="mt-n6" 
            variant="underlined"
            suffix="kg">
        </v-text-field>
        <span id="date">{{ entry.date }}</span>
        <button class="btn" id="btn_remove" @click="removeWeight">Remove</button>
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
}
</script>

<style scoped>
div {
    display: flex;
}

#ListWeight{
    display: flex;
    flex-direction: row;
    margin-bottom: 22.2px;
    padding-left: 20px;
    align-items: center;
}

#date {
    margin-right: 32px;
    font-style: italic;
}

#btn_remove{
  padding: 12px 17px;
  border-radius: 0 13px 13px 0;
}

</style>