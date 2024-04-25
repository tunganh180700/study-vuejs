<script>
export default {
  name: 'UITable',
  props: {
    titles: { type: Array },
    datas: { type: Array }
  }
}
</script>
<template>
  <div class="container">
    <h2>Game Management</h2>
    <ul class="responsive-table">
      <li class="table-header">
        <div class="col col-1" v-for="(title, i) in titles" :key="`${title}${i}`">
          {{ title }}
        </div>
      </li>
      <li class="table-row" v-for="(data, i) in datas" :key="`data-${data.name}`">
        <div class="col col-1" v-for="(title, i) in titles" :key="`${title}-${i}`">
          <slot :name="`column${i}`" :data="data"></slot>
        </div>
      </li>
    </ul>
  </div>
</template>
<style>
body {
  font-family: 'lato', sans-serif;
}
.container {
  width: 80%;
  margin-left: auto;
  margin-right: auto;
  padding-left: 10px;
  padding-right: 10px;
}

h2 {
  font-size: 26px;
  margin: 20px 0;
  text-align: center;
  small {
    font-size: 0.5em;
  }
}

.responsive-table {
  li {
    border-radius: 3px;
    padding: 25px 30px;
    display: flex;
    justify-content: space-between;
    margin-bottom: 25px;
  }
  .table-header {
    background-color: #95a5a6;
    font-size: 14px;
    text-transform: uppercase;
    letter-spacing: 0.03em;
  }
  .table-row {
    background-color: #ffffff;
    box-shadow: 0px 0px 9px 0px rgba(0, 0, 0, 0.1);
  }
  .col-1 {
    flex-basis: 40%;
  }
  .col-2 {
    flex-basis: 40%;
  }
  .col-3 {
    flex-basis: 25%;
  }

  @media all and (max-width: 767px) {
    .table-header {
      display: none;
    }

    li {
      display: block;
    }
    .col {
      flex-basis: 100%;
    }
    .col {
      display: flex;
      padding: 10px 0;
      &:before {
        color: #6c7a89;
        padding-right: 10px;
        content: attr(data-label);
        flex-basis: 50%;
        text-align: right;
      }
    }
  }
}
</style>
