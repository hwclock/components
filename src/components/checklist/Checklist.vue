<template>
  <div>
    <input type="text" v-model="inputGrupo" />
    <button @click="addGrupo">Adicionar grupo</button>
    <ul style="list-style-type: none;">
      <li v-for="(grupo, index) in checklist" :key="index">
        <s-list-grupo
          :grupo=grupo
        ></s-list-grupo>
        <ul style="list-style-type: none;">
          <li v-for="(item, index) in grupo.items" :key="index">
            <s-list-check :item_prop=item></s-list-check>
          </li>
        </ul>
      </li>
    </ul>

  </div>
</template>

<script>
import SListGrupo from './SListGrupo.vue';
import SListCheck from './SListCheck.vue';

export default {
    name: 's-checklist',

    components: {
        SListGrupo,
        SListCheck,
    },

    data: function () {
        return {
            showInputGrupo: false,
            inputGrupo: '',
            checklist: [],
        };
    },

    methods: {
        addGrupo() {
            if (this.inputGrupo != '') {
                this.checklist.push({
                    name: this.inputGrupo,
                    items: [],
                });
            }

            this.inputGrupo = '';
            this.showInputGrupo = false;
        },
    },
};
</script>

<style>
</style>