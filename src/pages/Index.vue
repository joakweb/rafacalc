<template>
  <q-page class="column q-pa-md">
    <div class="row justify-center q-my-lg">
      <div class="text-h2 text-grey-7">R$ {{ valorMaximo }}</div>
    </div>

    <q-btn
      push
      color="primary"
      label="Registrar compra"
      @click="toggleNovaCompra()"
    />

    <q-list
      bordered
      separator
      class="q-mt-lg rounded-borders"
    >
      <q-item
        clickable
        v-for="(compra, index) in comprasMesCorrente"
        :key="compra.index"
      >
        <q-item-section style="color:grey">{{ compra.nomeLoja }} - {{ compra.valorCompra }}</q-item-section>
        <q-item-section side>
          <q-btn
            round
            color="primary"
            icon="delete"
            @click="apagarCompra(index)"
          />
        </q-item-section>
      </q-item>
    </q-list>

    <q-dialog
      v-model="prompt"
      persistent
    >
      <q-card style="min-width: 350px">
        <q-card-section>
          <div class="text-h6">Nova compra</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          <q-input
            dense
            autofocus
            placeholder="Nome loja"
            @keyup.enter="prompt = false"
          />
        </q-card-section>

        <q-card-section class="q-pt-none">
          <q-input
            dense
            autofocus
            placeholder="Valor compra"
            @keyup.enter="prompt = false"
          />
        </q-card-section>

        <q-card-actions
          align="right"
          class="text-primary"
        >
          <q-btn
            flat
            label="Cancelar"
            v-close-popup
          />
          <q-btn
            flat
            label="Adicionar compra"
            v-close-popup
          />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      prompt: false,
      valorMaximo: 2500,
      comprasMesCorrente: [
        {
          nomeLoja: 'Mercadinho Brasileiro',
          valorCompra: 30.50
        },
        {
          nomeLoja: 'Pandara',
          valorCompra: 20.32
        },
        {
          nomeLoja: 'Preço Baixo',
          valorCompra: 86.50
        }
      ]
    }
  },
  methods: {
    apagarCompra (index) {
      this.comprasMesCorrente.splice(index, 1)
    },
    toggleNovaCompra () {
      this.prompt = !this.prompt
    }
  }
}
</script>
