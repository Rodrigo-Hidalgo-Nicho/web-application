<template>
    <h1>Notifications</h1>
    <div class="notifications">
     <br>
    <div class="today">
        <h3>Today</h3>
        <hr>
        <div class="activities">
            <pv-card class="activity">
                <template #content>
                    <div class="flex inline-block justify-content-around text-gray-700">
                        <span class="material-icons">sell</span>
                        <span>Promotion in shirts</span>
                        <div>
                            <pv-button>
                                CHECK
                            </pv-button>
                        </div>
                    </div>
                </template>
            </pv-card>
        </div>
    </div>
    <div class="yesterday">
        <h3>Yesterday</h3>
        <hr>
        <div class="activities">
            <pv-card class="activity">
                <template #content>
                    <div class="flex inline-block justify-content-around text-gray-700">
                        <span class="material-icons">mail</span>
                        <span>Provider request</span>
                        <div>
                            <pv-button>
                                CHECK
                            </pv-button>
                        </div>
                    </div>
                </template>
            </pv-card>
            <pv-card class="activity">
                <template #content>
                    <div class="flex inline-block justify-content-around text-gray-700">
                        <span class="material-icons">payments</span>
                        <span>Payment accepted</span>
                        <div>
                            <pv-button>
                                CHECK
                            </pv-button>
                        </div>
                    </div>
                </template>
            </pv-card>
            <pv-card class="activity">
                <template #content>
                    <div class="flex inline-block justify-content-around text-gray-700">
                        <span class="material-icons text-red-500">block</span>
                        <span>End: discount in scrubs</span>
                        <div>
                            <pv-button>
                                CHECK
                            </pv-button>
                        </div>
                    </div>
                </template>
            </pv-card>
        </div>
    </div>
    </div>
</template>

<script>

import {RandomUsersApiService} from "../../look-medico/services/random-user-api.services.js";

export default {
    name: "home",
    data(){
        return{
            user: [],
            errors: [],
            randomUserApi: new RandomUsersApiService()
        }
    },
    created() {
        console.log('created');
        this.getUser()
    },
    methods:{
        getUser(){
            this.randomUserApi.getUser()
                .then(response => {
                    this.user = response.data.results[0];
                    console.log(response.data.results[0])
                })
                .catch(error => {
                    this.errors.push(error);
                })
        }
    }
}
</script>

<style scoped>

h1{
    margin: 10px;
    font-size: 40px;
}
pv-avatar{
    width: 100px;
}
ul{
    text-align: left;
    list-style-type: none;
    margin: 0;
}

div.activities{

    text-align: center;
}

span{
    margin: 2px;

}

pv-card.activity{
    border-color: dimgray;
    border-radius: 20px;
    border-style: solid;
    margin: 0px;
    padding: 0;
}

pv-card.activity template span{
    font-size: 50px;
    color: dimgray;
}

div.my-activity{
    text-align: left;
    margin-right: 200px;
    margin-left: 200px;

}

pv-button{
    background-color: #25c6db;
}


</style>
