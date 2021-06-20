<template>
  <v-simple-table dark>
      <thead>
        <tr>
          <th class="text-left">
            Asset name
          </th>
          <th class="text-left">
            Department
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="item in inventories"
          :key="item.name_product"
        >
          <td>{{ item.name_product }}</td>
          <td>{{ item.department }}</td>
        </tr>
      </tbody>
  </v-simple-table>
  <p>
  <button @click="download">Download</button>
  </p>
</template>
<script>
import Papa from 'papaparse'
  export default {
    name: 'TableInventories',
    props: String,
    data () {
      return {
        inventories: [
          {
            name_product: 'Printer',
            department: 'HR',
          },
          {
            name_product: 'Monitor',
            department: 'IT',
          },
          {
            name_product: 'Barcode Scanner',
            department: 'ACCOUNT',
          },
        ],
      }
    },
    methods: {
      download() {
        let filename = 'inventories.csv';
        let text = Papa.unparse(this.inventories,{
          quotes: false, //or array of booleans
          quoteChar: '"',
          escapeChar: '"',
          delimiter: ",",
          header: true,
          newline: "\r\n",
          skipEmptyLines: false, //other option is 'greedy', meaning skip delimiters, quotes, and whitespace.
          columns: null //or array of strings
        });
                
        let element = document.createElement('a');
        element.setAttribute('href', 'data:text/csv;charset=utf-8,' + encodeURIComponent(text));
        element.setAttribute('download', filename);

        element.style.display = 'none';
        document.body.appendChild(element);

        element.click();
        document.body.removeChild(element)                                  
     }
    },
  }
</script>

