<template>
  <div class="container align-items-center" id="container">
    <div
      class="
        row
        justify-content-center
        align-items-center
        d-flex
        flex-column flex-md-row
        p-1
        m-1
      "
    >
      <h3>Busca Avançada</h3>
      <div class="col-9 col-md-6 col-sm-10 col-lg-5 col-xl-4 mb-sm-3">
        <input
          type="text"
          class="form-control mb-3"
          id="buscaFiltro"
          placeholder="Digite o nome do imovel"
          v-model="search"
        />
        <select id="filtrar" class="form-select mb-3" v-model="selected">
          <option
            v-for="(option, index) in options"
            :value="option.value"
            :key="index"
          >
            {{ option.text }}
          </option>
        </select>
        <select class="form-select mb-3" v-model="orderPrice">
          <option
            v-for="ordem in ordenacao"
            :key="ordem.text"
            :value="ordem.value"
          >
            {{ ordem.text }}
          </option>
        </select>
      </div>
      <div class="col-9 col-md-6 col-sm-10 col-lg-5 col-xl-4 mb-sm-3">
        <input
          type="number"
          id="minvalue"
          placeholder="Valor Minimo"
          class="form-control mb-3"
          v-model="minValue"
        />
        <input
          type="number"
          id="maxvalue"
          placeholder="Valor Máximo"
          class="form-control mb-3"
          v-model="maxValue"
        />
        <button
          type="button"
          class="button-clear btn col-12 mb-3"
          @click="limparFiltro"
        >
          Limpar Filtros
        </button>
      </div>
    </div>
    <div class="row m-2 m-sm-1 p-sm-1 p-2 d-flex flex-column listagem">
      <h1>Imoveis</h1>
      <div class="row flex-row mx-0 px-0 justify-content-center">
        <div
          class="imoveis col-10 col-sm-6 col-md-4 col-lg-3 mx-0 p-3"
          v-for="(imovel, id) in imoveisFiltered"
          :key="id"
        >
          <div class="card m-0 px-0 h-100">
            <img
              :src="require('../assets/Casa2.jpg')"
              class="card-img-top"
            />
            <div class="card-body">
              <h4 class="card-title">{{ imovel.nome }}</h4>
            </div>
            <ul class="list-group list-group-flush">
              <li class="list-group-item">Valor: R${{ imovel.valor }}</li>
              <li class="list-group-item">Tipo: {{ imovel.tipo }}</li>
            </ul>
            <div class="card-body">
              <a href="#" class="btn btn-primary">Detalhar</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Filtro",
  data() {
    return {
      search: "",
      selected: null,
      orderPrice: null,
      minValue: "",
      maxValue: "",
      options: [
        { value: null, text: "Filtrar por disponibilidade" },
        { value: true, text: "Disponível" },
        { value: false, text: "Indisponível" },
      ],
      ordenacao: [
        { value: null, text: "Ordenar por" },
        { value: "toMax", text: "Preço: Menor para maior" },
        { value: "toMin", text: "Preço: Maior para menor" },
      ],
      listaImoveis: [
        {
          id: 1,
          tipo: "casa",
          nome: "Casa 1 ",
          bairro: "Boa Vista",
          isActive: true,
          valor: 550,
        },
        {
          id: 2,
          tipo: "casa",
          nome: "Casa 2",
          bairro: "Centro",
          isActive: false,
          valor: 180,
        },
        {
          id: 3,
          tipo: "casa",
          nome: "Casa 3",
          bairro: "Cidade Nova",
          isActive: true,
          valor: 120,
        },
        {
          id: 4,
          tipo: "casa",
          nome: "Casa 4",
          bairro: "Boa Vista",
          isActive: true,
          valor: 170,
        },
        {
          id: 5,
          tipo: "apartamento",
          nome: "Apartamento 1",
          bairro: "Boa Vista",
          isActive: false,
          valor: 130,
        },
        {
          id: 6,
          tipo: "apartamento",
          nome: "Apartamento 2 ",
          bairro: "Mangabeiras",
          isActive: true,
          valor: 145,
        },
        {
          id: 7,
          tipo: "apartamento",
          nome: "Apartamento 3 ",
          bairro: "Boa Vista",
          isActive: true,
          valor: 180,
        },
        {
          id: 8,
          tipo: "apartamento",
          nome: "Apartamento 4 ",
          bairro: "Centro",
          isActive: true,
          valor: 200,
        },
        {
          id: 9,
          tipo: "chacara",
          nome: "Chacara 1 ",
          bairro: "Boa Vista",
          isActive: true,
          valor: 300,
        },
        {
          id: 10,
          tipo: "chacara",
          nome: "Chacara 2 ",
          bairro: "Boa Vista",
          isActive: false,
          valor: 400,
        },
        {
          id: 11,
          tipo: "chacara",
          nome: "Chacara 3 ",
          bairro: "Cidade Nova",
          isActive: true,
          valor: 450,
        },
        {
          id: 12,
          tipo: "chacara",
          nome: "Chacara 4 ",
          bairro: "Boa Vista",
          isActive: true,
          valor: 500,
        },
        {
          id: 13,
          tipo: "Loft",
          nome: "Loft 1 ",
          bairro: "Boa Vista",
          isActive: true,
          valor: 120,
        },
        {
          id: 14,
          tipo: "Loft",
          nome: "Loft 2 ",
          bairro: "Cidade Nova",
          isActive: true,
          valor: 140,
        },
        {
          id: 15,
          tipo: "Loft",
          nome: "Loft 3 ",
          bairro: "Boa Vista",
          isActive: true,
          valor: 180,
        },
        {
          id: 16,
          tipo: "Loft",
          nome: "Loft 4 ",
          bairro: "Mangabeiras",
          isActive: true,
          valor: 70,
        },
      ],
    };
  },
  computed: {
    imoveisFiltered() {
      let imoveisFiltrados = [];
      imoveisFiltrados = this.listaImoveis.filter((imovel) => {
        return (
          imovel.nome.toLowerCase().indexOf(this.search.toLowerCase()) > -1
        );
      });
      imoveisFiltrados = imoveisFiltrados.filter((imovel) => {
        if (this.selected === null) {
          return imovel;
        }
        return imovel.isActive === this.selected;
      });
      if (this.minValue && this.maxValue) {
        imoveisFiltrados = imoveisFiltrados.filter((imovel) => {
          if (imovel.valor >= this.minValue && imovel.valor <= this.maxValue) {
            return imovel;
          }
        });
      }
      if (this.orderPrice === "toMax") {
        imoveisFiltrados.sort(function (a, b) {
          if (a.valor < b.valor) {
            return -1;
          } else {
            return true;
          }
        });
      } else if (this.orderPrice === "toMin") {
        imoveisFiltrados.sort(function (a, b) {
          if (a.valor > b.valor) {
            return -1;
          } else {
            return true;
          }
        });
      }
      return imoveisFiltrados;
    },
  },
  methods: {
    limparFiltro() {
      this.search = "";
      this.selected = null;
      (this.minValue = ""), (this.maxValue = "");
    },
  },
};
</script>


<style scoped>
.imoveis > div {
  box-shadow: 5px 5px 8px 5px rgba(7, 6, 6, 0.384);
  border: none;
  border-radius: 0;
  transition: all 0.8s;
}

.imoveis > div:hover {
  transform: translateY(-5px);
  transition: all 0.8s;
}

#container {
  border-radius: 15px;
}

.button-clear {
  background: rgb(52, 175, 247);
  color: white;
}

h1,
h3 {
  font-family: "Anek Kannada", sans-serif;
}

h1 {
  font-size: 4rem;
}

.listagem {
  background-color: rgba(243, 237, 237, 0.637);
  border-radius: 20px;
}
</style>
