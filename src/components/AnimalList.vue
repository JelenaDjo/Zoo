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
            <button type="submit">Add Animal</button>
        </form>

        <h1> Animal List </h1>
        <table border=1>
            <thead>
                <th>Broj</th>
                <th> Ime</th>
                <th>Vrsta</th>
                <th>Datum rodjenja</th>
            </thead>
            <tbody>
                <tr v-for="(animal, index) in animals" :key="index">
               <td>{{ index +1}}</td>
                <td>{{animal.name}}</td>
                <td>{{animal.species}}</td>
                <td>{{animal.date ? animal.date: 'Nepostoji'}}</td>
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
export default {
    data(){
        return { 
        newAnimal: {
            species: '',
            name: '',
            date: ''
            },

        animals: [
            {name: 'Cicko', species: 'Pas', date: '20/10/2015'},
            {name: 'Hulk', species: 'Zec'},
            {name: 'Barni', species: 'Hrcak', date: '12/08/2009'},
            {name: 'Fredy', species: 'Guster'},
            {name: 'Beba', species: 'Macka', date: '18/05/2013'}

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

