<template>
  <div id="slogan">
    <div class="text-center">
      <h1 >Name Generator
      <h6 class="text-secondary">Gerador de nomes utilizando Vue.js, GraphQL e NodeJS</h6>
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
                    {{ prefix }}
                  </li>
                </ul>
                <br />  
                <input class="form-control" type="text" placeholder="Digite o prefixo" />
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
                    {{ sufix }}
                  </li>
                </ul>
                <br />
                <input class="form-control" type="text" placeholder="Digite o Sufixo" />
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
      prefixes: ['Air', 'Jet', 'Flight'],
      sufixes: ['Hub', 'Station', 'Mart'],
      domains: ['AirHub', 'AirStation', 'AirMart', 'JetHub', 'JetStation', 'JetMart', 'FlightHub', 'FlightStation', 'FlightMart']
    }
  }
}
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
