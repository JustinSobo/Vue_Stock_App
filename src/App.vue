<template>

  <main>
    
    <div class="header-wrapper">
      <div class="header-container">
        <div class="header">
          $tock Price App 
        </div>
      </div>
    </div>

    <div class="search-wrapper">
      <div class="search-container">
        <input 
          type="text" 
          class="search" 
          placeholder="Search . . ."
          v-model="query"
          @keypress="fetchStock"
          />
      </div>
    </div>

    <div class="stock-wrapper">
      <div class="stock-container">
        <div class="stock">
     
          <div class="stock-row-1">
            <div class="stock-item">
              <div class="stock-item-label">Name</div>
              <div class="stock-item-symbol-data stock-item-data">{{ stock.symbol }}</div>
            </div>

            <div class="stock-item">
              <div class="stock-item-label">Open</div>
              <div class="stock-item-open-data stock-item-data">{{ stock.open }}</div>
            </div>
          </div>

          <div class="stock-row-2">
            <div class="stock-item">
              <div class="stock-item-label">High</div>
              <div class="stock-item-open-data stock-item-data">{{ stock.high }}</div>
            </div>
            <div class="stock-item">
              <div class="stock-item-label">Low</div>
              <div class="stock-item-low-data stock-item-data">{{ stock.low }}</div>
            </div>
          </div>

          <div class="stock-row-3">
            <div class="stock-item">
              <div class="stock-item-label">Close</div>
              <div class="stock-item-close-data stock-item-data">{{ stock.close }}</div>
            </div>
            <div class="stock-item">
              <div class="stock-item-label">Volume</div>
              <div class="stock-item-volume-data stock-item-data">{{ stock.volume }}</div>
            </div>
          </div>
          
        </div>
      </div>
    </div>

    <footer>
      <div class="footer-wrapper">
        <div class="footer-container">
          <div class="footer">
            J S G r a p h i x
          </div>
        </div>
      </div>
    </footer>


  </main>

</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      url_base: 'https://api.polygon.io/v1/open-close/',
      query: '',
      range: '/2020-10-14',
      adjusted: '?adjusted=true',
      api_base: '&apiKey=',
      api_key: 'ocfCoPkAjhBpbUemNDwzIWe7hL7ipooS',
      stock: {}
    }
  },
  methods: {
    fetchStock (e) {
      if (e.key == "Enter") {
        fetch(`${this.url_base}${this.query.toUpperCase()}${this.range}${this.adjusted}${this.api_base}${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(this.setresult);
      }
    },
    setresult (result) {
      this.stock = result;
    },
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@200;400;700&family=Share+Tech+Mono&family=VT323&display=swap');

@font-face {
    font-family: 'TheNextFont';
    src: url('./assets/thenextfont-webfont.woff2') format('woff2'),
         url('./assets/thenextfont-webfont.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}

html {
  background-color: #000000;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  background-color: #000000;
  
  background-size: cover;
  border-radius: .5em;
}

main {
  min-height: 100vh;
  padding: 1em;
  
  border-radius: 1em;
}

.header-container {
  width: 100%;
  border-radius: 1em;

}

.header {
  font-family: 'Oswald', sans-serif;
  font-weight: 700;

  color: rgba(120, 224, 143,1.0);
  font-size: 2.5em;
  text-transform: uppercase;

  text-shadow: 5px 5px 0px rgba(120, 224, 143, 0.2);

  padding: .5em;
  text-align: center;
}

.search-container {
  width: 100%;
  margin-top: 1em;

}

.search {
  font-family: 'Oswald', sans-serif;
  font-weight: 400;
  color: #0be881;
  font-size: 1.125em;
  text-transform: uppercase;

  border-radius: 1em;
  background-color: rgba(255, 255, 255, 0);
  
  border-style: solid;
  border-width: 1px;
  border-color: rgba(120, 224, 143,1.0);

  width: 100%;

  padding: 1em;
}

::placeholder {
  color: rgba(120, 224, 143,1.0);
  font-family: 'Oswald', sans-serif;
  font-weight: 400;
  text-transform: uppercase;
}

.stock {
  font-family: 'Oswald', sans-serif;
  font-weight: 400;
  color: #ffffff;
  font-size: 1.25em;
}

.stock-row-1 {
  display: flex;
  margin-top: 1em;
  margin-left: -.5em;
  margin-right: -.5em;
}

.stock-row-2 {
  display: flex;
  margin-left: -.5em;
  margin-right: -.5em;
}

.stock-row-3 {
  display: flex;
  margin-left: -.5em;
  margin-right: -.5em;
}

.stock-item {
  background-color: rgba(120, 224, 143,1.0);
  border-radius: 1em;
  margin: .5em;
  min-height: 6em;
  width: 50%;

  border-color: rgba(0, 0, 0, .2);
  border-width: 2px;
  border-style: solid;

  color: #000000;
}

.stock-item-label {
  font-family: 'Oswald', sans-serif;
  font-weight: 700;
  text-transform: uppercase;
  font-size: 1.125em;
  color: #000000;
  text-align: left;

  margin-top: 1em;
  margin-left: .5em;
  padding-left: .5em;

  text-shadow: 3px 3px 0px rgba(0, 0, 0, 0.15);
}

.stock-item-data {
  font-family: 'Share Tech Mono', monospace;
  text-transform: uppercase;
  font-size: 1.25em;
  color: #000000;
  text-align: left;
  margin-left: .5em;
  padding-left: .5em;

  text-shadow: 2px 2px 0px rgba(0, 0, 0, 0.15);

}

.footer {
  font-family: 'TheNextFont';
  color: rgba(120, 224, 143,1.0);
  text-align: center;
  margin-top: 2em;
}
</style>

```
- Header
- Searchbox
- Stock
  > Name: 
  > Symbol: 
  > Open: 
  > High: 
  > Low: 
  > Close: 
  > Volume: 

font-family: 'Oswald', sans-serif;
font-family: 'Share Tech Mono', monospace;
font-family: 'VT323', monospace;

```
