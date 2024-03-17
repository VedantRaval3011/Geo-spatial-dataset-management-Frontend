<template>
  <div class="mainContainer">
    <div class="top-container">
      <div class="logo">
        <img src="../assets/vedas.png" alt="vedas logo" />
      </div>
      <div class="user">
        <img class="user-button" src="../assets/userbg.png" alt="user-image" />
      </div>
    </div>
    <div class="upper-container">
        <div class="button-back">
          <button>Back</button>
        </div>
        <div class="heading">

        <h1>Primary Data Management</h1>
        
        <input type="text" v-model="searchQuery" placeholder="Search..." /> 
        </div>
        <div class="add-button">
            <button @click="$router.push('/primary-data-management')">Add data</button>
        </div>
    </div>
    <div class="table-container">
      <div class="scrollable-table">
        <table>
          <thead>
            <tr>
              <th>ID</th>
              <th>Name of Dataset</th>
              <th>Action</th>
            </tr>
          </thead>
          <tbody>
            <!-- Rows will be dynamically added here -->
            <tr v-for="row in filteredRows" :key="row.id">
              <td>{{ row.id }}</td>
              <td>{{ row.name }}</td>
              <td><button>Edit</button></td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: '',
      rows: [
        { id: 1, name: 'Dataset 1' },
        { id: 2, name: 'Dataset 2' },
        { id: 3, name: 'Dataset 3' },
        { id: 4, name: 'Dataset 4' },
        { id: 5, name: 'Dataset 5' },
        { id: 6, name: 'Dataset 6' },
        { id: 4, name: 'Dataset 4' },
        { id: 5, name: 'Dataset 5' },
        { id: 6, name: 'Dataset 6' },
        // Add more rows as needed
      ]
    };
    },
  computed: {
    filteredRows() {
      return this.rows.filter(row => row.name.toLowerCase().includes(this.searchQuery.toLowerCase()));
    }
  }
  
}
</script>

<style scoped>
    .top-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  padding: 0;
  background: inherit;
  display: flex;
  justify-content: space-between;
}

.mainContainer{
   
  display: flex;
  flex-direction: column;
  justify-content: center;
  
  height: 100vh;
  width: 100%;
  background: linear-gradient(
    to right,
    #c3e5f9,
    #bae1f6,
    #b0dcf3,
    #a6d8f0,
    #9cd4ed,
    #93d1eb,
    #89cde8,
    #7fcae6,
    #73c6e4,
    #67c2e3,
    #59bee1,
    #49bae0
  ); /* Gradient background */
}

.upper-container{
  display: flex;
  justify-content: center;
  margin-top: 100px;
  gap: 130px;
}
.logo {
  margin-right: 20px; /* Add some spacing between the logo and other content */
  position: fixed;
}

.logo img {
  margin-left: 20px;
}

.add-button{
  margin-top: 80px;
}
.user-button {
  width: 80px;
  margin: 33px;
  border-radius: 50%; /* Add rounded corners */
  box-shadow: 0px 1px 5px rgb(94, 77, 77);
  position: fixed;
  right: 0
}

.button-back{
  position: relative;
  top: 80px;
}

button {
  --clr-font-main: hsla(0 0% 20% / 100);
  --btn-bg-1: hsla(194 100% 69% / 1);
  --btn-bg-2: hsla(217 100% 56% / 1);
  --btn-bg-color: hsla(360 100% 100% / 1);
  --radii: 0.5em;
  cursor: pointer;
  
  min-width: 120px;
  min-height: 44px;
  font-size: var(--size, 1rem);
  font-family: "Segoe UI", system-ui, sans-serif;
  font-weight: 500;
  transition: 0.8s;
  background-size: 280% auto;
  background-image: linear-gradient(325deg, var(--btn-bg-2) 0%, var(--btn-bg-1) 55%, var(--btn-bg-2) 90%);
  border: none;
  width: 50px;
  border-radius: var(--radii);
  color: var(--btn-bg-color);
  box-shadow: 0px 0px 20px rgba(71, 184, 255, 0.5), 0px 5px 5px -1px rgba(58, 125, 233, 0.25), inset 4px 4px 8px rgba(175, 230, 255, 0.5), inset -4px -4px 8px rgba(19, 95, 216, 0.35);
}

button:hover {
  background-position: right top;
}

button:is(:focus, :focus-visible, :active) {
  outline: none;
  box-shadow: 0 0 0 3px var(--btn-bg-color), 0 0 0 6px var(--btn-bg-2);
}

@media (prefers-reduced-motion: reduce) {
  button {
    transition: linear;
  }
}


.form-container-6{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.table-container {
  margin-top: 20px;
  position: relative;
  left: 35px;
  
 
}

.scrollable-table {
  max-height: 400px; /* Adjust the height as needed */
  overflow-y: auto;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  padding: 20px;
}

table {
  width: 75%;
  border-collapse: collapse;
  background-color: transparent;
}

thead th {
  background-color: #eee;
}

tbody tr:nth-child(even) {
  background-color: #f2f2f2;
}

tbody tr:nth-child(odd) {
  background-color: #ddd;
}

td,
th {
  padding: 10px;
}

.input-container {
  margin-top: 10px;
}

input[type="text"] {
  padding: 8px;
  border-radius: 4px;
  border: 1px solid #ccc;
  width: 300px;
}

.user-button:hover {
  box-shadow: 0px 0px 0px rgb(94, 77, 77);
  cursor: pointer;
  z-index: 20;
}



.user-button {
  --clr-font-main: hsla(0 0% 20% / 100);
  --btn-bg-1: rgb(65, 145, 249);
  --btn-bg-2: hsla(194 100% 56% / 1);
  --btn-bg-color: hsla(360 100% 100% / 1);
  --radii: 0.5em;
  cursor: pointer;
  min-width: 120px;
  font-size: var(--size, 1rem);
  font-family: "Segoe UI", system-ui, sans-serif;
  font-weight: 500;
  transition: 0.8s;
  background-size: 280% auto;
  border: none;
  width: 50px;
  border-radius: 50%;
  color: var(--btn-bg-color);
  box-shadow: 0px 0px 20px rgba(71, 184, 255, 0.5), 0px 5px 5px -1px rgba(58, 125, 233, 0.25), inset 4px 4px 8px rgba(175, 230, 255, 0.5), inset -4px -4px 8px rgba(19, 95, 216, 0.35);
}




</style>