<script>
import Sidebar from "./components/Sidebar.vue";


export default{
    name: "App",
    components: { 
    Sidebar 
    },
  data(){
        return{
            transactionData : ""
        }
    },
    methods: {
        async fetchData() {
            var myHeaders = new Headers();
            myHeaders.append("Content-Type", "application/json");
            myHeaders.append("Cookie", "JSESSIONID=503A44513198B8F7894A9DF8032C02A9");

            var raw = JSON.stringify({
            "request": {
                "fromDate": "01/01/19", 
                "toDate": "01/31/19" 
            }
            });

            var requestOptions = {
            method: 'POST',
            headers: myHeaders,
            body: raw,
            redirect: 'follow'
            };

            const url = `${"http://ws1.e1-vhp.com:8080/VHPWebBased1/rest/Common/testWebdev"}`
            this.transactionData = await (await fetch(url, requestOptions)).text();
            console.log(JSON.parse(this.transactionData).response.outletTransaction['outlet-transaction']);
            
        }, 
    }
}

</script>
  

<template>
<div class="induk">
  <div class="sidebar">
    <Sidebar @get-data = "fetchData"/>  
  </div>
  <div>
    <br>
    <br>
    <table>
      <tbody>
        <tr>
          <th>Transaction Date</th>
          <th>Departement</th>
          <th>Waiter Name</th>
          <th>Table Number</th>
          <th>Bill Number</th>
          <th>Guest Name</th>
          <th>Pax</th>
          <th>Total Amount</th>
        </tr>
        <tr>
          <td>2018</td>
          <td>1</td>
          <td>pal3</td>
          <td>10</td>
          <td>15691</td>
          <td>SULFIA, MEKA MS</td>
          <td>2</td>
          <td class="amount">300000</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>
</template>

<style>
  tbody td, tbody th {
    padding: 10px;
    border: 1px solid lightgrey;
  }
  tbody tr th {
    color: aliceblue;
    background: rgb(90,137,213);
    background: linear-gradient(180deg, rgba(90,137,213,1) 0%, rgba(0,37,249,1) 100%);
    /* border-radius: 10px 10px 0px 0px; */
  }
  .induk{
    display: flex;
  }
  .sidebar{
    width: 17%;
    margin-right: 20px;
    border-right: 2px solid lightgrey;
    height: 100vh;
  }
  .amount{
    text-align: right;
  }
</style>