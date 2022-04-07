<template>

  <h1>Registro Spese</h1>

    <div class="contenitore">
        <div id="DescriptionDiv">
            <h3 style="color:rgb(16, 16, 73), rgb(39, 41, 156)"> Descrizione spesa </h3>
            <input type="text" id="description" v-model="expense">
        </div>
        
        <div class="btn">
            <button id="button" @click="addExpense">Aggiungi</button>
        </div>
        
        <div id="ImportoDiv">
            <h3 style="color:rgb(16, 16, 73), rgb(39, 41, 156)"> Importo Spesa </h3>
            <input type="number" id="amount" placeholder="€" v-model="amount">
        </div>
        
    </div>

    
    <table>
        <tr>
            <th style="width:60%">Descrizione spesa</th>
            <th>Importo</th>
            <th>Azioni</th>
        </tr>

        <tr>
            <td>{{placeholder}}<div class="tableDiv" v-for="(expense, index) in Expenses" :key="index">{{expense.name}}</div></td>
            <td><div class="tableDiv" v-for="(amount, index) in Amounts" :key="index">€ {{amount.name}}</div></td>
            
            <td><div class="tableDiv" v-for="(expense, index) in Expenses" :key="index">
                <svg id="trash" @click=" deleteExpense(index), checkEmpty()" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><!--! Font Awesome Pro 6.1.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. --><path d="M135.2 17.69C140.6 6.848 151.7 0 163.8 0H284.2C296.3 0 307.4 6.848 312.8 17.69L320 32H416C433.7 32 448 46.33 448 64C448 81.67 433.7 96 416 96H32C14.33 96 0 81.67 0 64C0 46.33 14.33 32 32 32H128L135.2 17.69zM394.8 466.1C393.2 492.3 372.3 512 346.9 512H101.1C75.75 512 54.77 492.3 53.19 466.1L31.1 128H416L394.8 466.1z"/></svg>
                </div>
            </td>
            
        </tr>


    </table>


</template>

<script>
export default {
    data(){
        return{
            expense: '',
            amount: '',
            placeholder: "Non hai aggiunto nulla alla lista",
            Expenses: [],
            Amounts: []
        }
    },

    methods:{
        addExpense(){

            if(this.expense.length != 0 && this.amount != 0)

                this.Expenses.push({
                name : this.expense
                 
            }),
            
                this.Amounts.push({
                name : this.amount 
            }) 
            
            this.expense = '',
            this.amount = '',
            this.placeholder = null
            
        },

        deleteExpense(index){
            
            this.Expenses.splice(index,1),
            this.Amounts.splice(index,1)
            
        },

        checkEmpty(){
            if(this.Expenses.length === 0){
                this.placeholder = "Non hai aggiunto nulla alla lista"
            }
        }

        
    }
}
</script>


<style>

.contenitore{
    display: grid;
    width: 800px;
    height: 150px;
    grid-template-columns: repeat(3, 1fr);
    margin: 0 auto;
    border: 1px solid;
    border-radius: 16px;
    background-image: linear-gradient(to right, rgb(59, 167, 255), rgb(98, 184, 255));
}

.btn{
    margin-top: auto;
    margin-bottom: 20px;
    
}

#button{
    border-radius: 16px;
}

table, th, td{
    margin-top: 50px;
    margin-left: auto;
    margin-right: auto;
    width: 800px;
    border: 1px solid #333;
    border-collapse: collapse;  
    padding: 5px; 
    background-color: white;
}

.tableDiv{
    padding: 10px;
}

#trash{
    width: 15px;
}

input{
    border-radius: 16px;
}

#DescriptionDiv{
    margin-left: 160px;
}

#ImportoDiv{
    margin-right: 160px;
}

</style>
