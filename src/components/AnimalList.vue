<template>
    <div>
        <h2> Add Animal </h2>
        <form @submit.prevent="addAnimal">
            <label>Name</label>
            <input v-model="newAnimal.name" placeholder="Name"> <br/>

            <label>Species</label>
            <input v-model="newAnimal.species" placeholder="Species"> <br/>

            <label>Date Of Birth</label>
            <input v-model="newAnimal.date" placeholder="Date Of Birth"><br/>

            <select v-model="newAnimal.sector">
                <option disabled value="">Please choose one</option>
                <option v-for="(sector, index) in sectors" :key="index" :value="sector">{{sector.name}}</option>
            </select>

            <button type="submit">Add Animal</button>
        </form>

        <h1> Animal List </h1>
        <table border=1>
            <thead>
                <th>Broj</th>
                <th> Ime</th>
                <th>Vrsta</th>
                <th>Datum rodjenja</th>
                <th>Sector</th>
            </thead>
            <tbody>
                <tr v-for="(animal, index) in animals" :key="index">
               <td>{{ index +1}}</td>
                <td>{{animal.name}}</td>
                <td>{{animal.species}}</td>
                <td>{{animal.date ? animal.date: 'Nepostoji'}}</td>
                <td>{{animal.sector.name}}</td>
                <td>
                    <button @click="removeAnimal(animal)" type="submit"> Remove </button>
                </td>
                <td>
                    <button @click="moveToTop(animal)" type="submit"> Move to top </button>
                </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>



<script>

const sectors = [
    {name: 'Home animals', surface: 'Home'},
    {name: 'Air animals', surface: 'Air'},
    {name: 'Water animals', surface: 'Water'}


]
export default {
    data(){
        return { 
        sectors: sectors,
        
        newAnimal: { },


        animals: [
            {name: 'Cicko', species: 'Pas', date: '20/10/2015', sector:sectors[0]},
            {name: 'Hulk', species: 'Zec', sector:sectors[0]},
            {name: 'Barni', species: 'Papagaj', date: '12/08/2009', sector:sectors[1]},
            {name: 'Fredy', species: 'Delfin', sector:sectors[2]},
            {name: 'Beba', species: 'Albatros', date: '18/05/2013', sector:sectors[1]}

        ]
        }
    },
    methods: {
        removeAnimal(animal){
            let index = this.animals.indexOf(animal);
            this.animals.splice(index, 1);
        },
        moveToTop(animal){
            let index1 = this.animals.indexOf(animal);
                        this.animals.splice(index1, 1);

            this.animals.unshift(animal);
           
        },
         addAnimal() {
            this.animals.push(this.newAnimal);
            this.newAnimal = {};
    }
    
}
}

</script>

