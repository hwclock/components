<template>
    <div>
        <input
            type="checkbox"
            :checked=item.value
            @click="item.value = !item.value"
        />
        <label class="checks"
            :style="`text-decoration: ${item.value ? 'line-through' : 'none'};`"
        >{{ item.name }}</label>
        <i class="mdi backspace-outline">X</i>
    </div>
</template>

<script>
export default {
    name: 's-list-check',

    data() {
        return {
            item: this.item_prop,
        };
    },

    props: {
        item_prop: Object, default: () => {},
    },
};
</script>

<style scoped>

div {
    margin-top: 15px;
}

.checks {
    padding: 0px 5px;
}
</style>