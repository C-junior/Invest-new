<template>
  <q-page class="flex flex-center">
    <div class="disp">
      <div v-if="totalcap >= 0" > Você terá ao final de {{year}} meses:</div>
    <div class="restotal" v-if="totalcap >= 0"  > {{totalcap.toLocaleString('pt-br',{style: 'currency', currency: 'BRL'})}} </div>
    <!-- <div class="restotal" v-else-if="totalm >= 0" >{{ 'R$ ' + totalm}} </div> -->
     <div class="restotal" v-else >{{ 'R$ ' + '0'}} </div>
     <!-- <div v-if="totalcap >= 0" > e o seu rendimento vai ser de R$ {{ parseInt(rendimento) + parseInt(rendpar)}}</div> -->
    </div>
    <div class="divider"></div>
    <div class="blok">
    <div>
      Capital inical investido
    </div>
    <input type="tel"  v-on:input="capital = parseInt($event.target.value)" placeholder="Caso não haja, deixe vazio" >
    </div>
    <div class="blok">
    <div>
      Valor a ser investido todos os meses
    </div>
    <input type="tel" v-on:input="mes = parseInt($event.target.value)"  placeholder="Caso não haja, deixe vazio">
    <!-- <input v-if="selected == 1" v-on:input="mesm = parseInt($event.target.value)" > -->
    </div>
    <div class="blok">
    <div >Quantidade de meses que deseja investir</div>
    <input type="tel" v-on:input="year = parseInt($event.target.value)" >
    <!-- <div @click="selected = 2" :class="{active:selected == 2}" class="btn">Anos</div> -->
    </div>
    <!-- <input v-if="selected == 1" v-on:input="meses = parseInt($event.target.value)" placeholder="Meses" > -->
    <div class="blok">
      <div>
      Qual a taxa de rendimento anual do seu investimento
    </div>
    <input type="tel" v-on:input="rmensal = parseFloat($event.target.value)" placeholder="Somente o valor sem %">
    <!-- <input v-if="selected == 1" v-on:input="rmensalm = parseFloat($event.target.value)"> -->
    </div>
    <q-footer reveal elevated class=" footer text-white">
      <q-toolbar>
        <q-toolbar-title>
    <div class="texto-f">
     made by &nbsp; <span> Khaoz Corp.</span>
    </div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
    <img class="coin-bg" :src="img.icon" alt="" >
    <div class="hide">
      {{rendimento = mes * yearm - total}}
    {{rcap.toFixed(2)}}
    {{rendpar = rcap - capital }}
      {{cap1 = 1 + percent}}
      {{cap2 = cap1 ** yearm}}
      {{rcap = cap2 * capital}}
      {{mes1 = mes * year}}
    {{yearm = year }}
    {{ranual = rmensal / 12}}
     {{ percent = ranual / 100 }} -- {{tax = 1+ percent}} --
     {{r2 = tax ** yearm}} -- {{r3 = r2 - 1}}
     {{r4 = mes * r3}}
     <span > {{res = r4 / percent}} </span>
     {{total = res.toFixed(2)}}
     {{rescap = rcap.toFixed(2)}}
      {{totalcap = parseInt(rescap) + parseInt(total)}}
     <!-- meses
     {{ percentm = rmensalm / 100 }} -- {{taxm = 1+ percentm}} --
     {{r2m = taxm ** meses}} -- {{r3m = r2m - 1}}
     {{r4m = mesm * r3m}}
     <span > {{resm = r4m / percentm}} </span>
     {{totalm = resm.toFixed(2)}}-->
    </div>
  </q-page>
</template>

<script>

export default {
  name: 'PageIndex',
  data () {
    return {
      value: 123,
      capital: 0,
      rcap: 0,
      totalcap: 0,
      mes: 0,
      year: 0,
      yearm: 0,
      meses: 0,
      rmensal: 0,
      rendimento: 0,
      rendpar: 0,
      ranual: 0,
      rmensalm: 0,
      percent: 0,
      tax: 0,
      res: 0,
      r2: 0,
      r3: 0,
      r4: 0,
      total: 0,
      rescap: 0,
      img: {
        icon: require('../assets/coin.png'),
        logo: require('../assets/invest-icon.png')
      },
      active: true,
      selected: 0
    }
  },
  methods: {
    function () {
      if (this.rescap <= 0) {
        this.rescap = 0
      }
    }
  },
  mounted () {
  }
}

</script>
