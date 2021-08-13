<template>
  <div id="slogan">
    <div class="text-center">
      <h1 >Domain Generator
      <h6 class="text-secondary">Gerador de dominíos utilizando Vue.js, GraphQL e NodeJS</h6>
      </h1>
    </div>

    <div id="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <h5>
              Prefixos 
              <div class="badge bg-info">{{ prefixes.length }}</div>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul 
                  class="list-group"
                >
                  <li 
                    class="list-group-item"
                    v-for="prefix in prefixes"
                    :key="prefix"
                  >
                    <div class="row">
                      <div class="col-md">
                        {{ prefix }}
                      </div>
                      <div class="col-md text-end">
                        <button 
                          class="btn btn-danger"
                          @click="deletePrefix(prefix)"
                        >
                          <span class="fa fa-trash"></span>
                        </button>
                      </div>
                    </div>
                  </li>
                </ul>
                <br />  
                <div class="input-group">
                  <input 
                    class="form-control" 
                    type="text" 
                    placeholder="Digite o prefixo" 
                    v-model="prefix"
                    v-on:keyup.enter="addPrefix(prefix)"
                  />
                  <div class="input-group-append">
                    <button 
                      class="btn btn-info"
                      @click="addPrefix(prefix)"
                    >
                      <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-md">
            <h5>
              Sufixos
              <div class="badge bg-info">{{ sufixes.length }}</div>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li 
                    class="list-group-item"
                    v-for="sufix in sufixes"
                    :key="sufix"
                  >
                    <div class="row">
                      <div class="col-md">
                        {{ sufix }}
                      </div>
                      <div class="col-md text-end">
                        <button 
                          class="btn btn-danger"
                          @click="deleteSufix(sufix)"
                        >
                          <span class="fa fa-trash"></span>
                        </button>
                      </div>
                    </div>
                  </li>
                </ul>
                <br />
                <div class="input-group">
                  <input 
                    class="form-control" 
                    type="text" 
                    placeholder="Digite o sufixo" 
                    v-model="sufix"
                    v-on:keyup="addSufix(sufix)"
                  />
                  <div class="input-group-append">
                    <button 
                      class="btn btn-info"
                      @click="addSufix(sufix)"
                    >
                      <span class="fa fa-plus"></span>
                    </button>
                  </div>
                </div>                
              </div>
            </div>
          </div>
        </div>
      </div>
      <br/>
      <div class="container">
        <h5>
          Dominíos disponíveis
          <span class="badge bg-info">{{ domains.length }}</span>
        </h5>
        <div class="card">
        <div class="card-body">
          <ul class="list-group">
            <li 
              class="list-group-item"
              v-for="domain in domains"
              :key="domain"
            >
              {{ domain }}.com.br
            </li>
          </ul>
        </div>
      </div>
      </div>
    </div>
  </div>

</template>

<script>
import 'bootstrap/dist/css/bootstrap.css';
import 'font-awesome/css/font-awesome.css';

export default {
	name: 'App',
	data: function () {
		return {
      disabled: true,
      prefix: '',
      sufix: '',
			prefixes: ['Air', 'Jet', 'Flight'],
			sufixes: ['Hub', 'Station', 'Mart'],
			domains: ['AirHub', 'AirStation', 'AirMart', 'JetHub', 'JetStation', 'JetMart', 'FlightHub', 'FlightStation', 'FlightMart']
		};
	},
  methods: {
    addPrefix(prefix) {
      this.prefixes.push(prefix);
      this.prefix = ''
      this.generate();
    },
    addSufix(sufix) {
      this.sufixes.push(sufix);
      this.generate();
    },
    deletePrefix(prefix) {
      this.prefixes.splice(this.prefixes.indexOf(prefix), 1);
      this.generate();
    },
    deleteSufix(sufix) {
      this.sufixes.splice(this.sufixes.indexOf(sufix), 1)
      this.generate();
    },
    generate() {
      this.domains = [];
      for (const prefix of this.prefixes) {
        for (const sufix of this.sufixes) {
          this.domains.push(prefix + sufix);
        }
      }
    }
  }
};
</script>

<style scoped>
  #slogan {
    margin-top: 30px;
    margin-bottom: 30px;
  }
  #main {
    background-color: #f3f5f4;
    padding: 30px 0;
  }
</style>
