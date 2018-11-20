<template>
    <div>
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
                    <button @click="removeAnimal(animal)"> Remove </button>
                </td>
                <td>
                    <button @click="moveToTop(animal)"> Move to top </button>
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
           
        }
    }
    
};
</script>

