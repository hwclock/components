<template>
    <div class="grupo">
        <i class="mdi plus-circle-outline" @click="showInput = !showInput">+</i>
        <label>{{ grupo.name }}</label>&nbsp;&nbsp;
        <i class="mdi backspace-outline">X</i>
        <div v-if="showInput">
            <input type="text" v-model="input" placeholder="Digite..."/>
            <i class="mdi arrow-down-right-bold" @click="addProp">↓</i>
        </div>
    </div>
</template>

<script>
export default {
    name: 's-list-grupo',

    data() {
        return {
            showInput: false,
            input: '',
        };
    },

    props: {
        grupo: Array, default: () => {
            return {
                'name': '',
                'items': [],
            };
        },
    },

    methods: {
        addProp() {
            if (this.input != '') {
                // eslint-disable-next-line vue/no-mutating-props
                this.grupo.items.push({
                    'name': this.input,
                    'value': false,
                });
            }

            this.input = '';
            this.showInput = false;
        },
    },
};
</script>

<style scoped>
.grupo {
    background-color: transparent;
    border: 1px solid gray;
    min-width: 120px;
    border-radius: 13px;
    padding: 5px 10px;
    margin-top: 20px;
    max-width: 300px;
}
</style>