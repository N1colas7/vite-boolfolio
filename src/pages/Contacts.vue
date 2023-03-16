<script>
    import axios from 'axios';

export default {

    name: 'Contacts',
    data() {
        return {
            name:'',
            surname: '',
            email: '',
            phone:'',
            message:'',
            errors:null
        }
    },
    methods:{
        sendForm(){
            const data = {
                name: this.name,
                surname: this.surname,
                email: this.email,
                phone: this.phone,
                message: this.message,                
            }

            axios.post(`${this.store.baseUrl}/api/contacts`,data).then((response) => {
                if(!this.success){
                    this.errors = response.data.errors
                }
                else{
                    this.name ='';
                    this.surname = '';
                    this.email = '';
                    this.phone ='';
                    this.message ='';
                }
            });
        }
    }
}
</script>
<template lang="">
    <div class="container">
        <div class="row my-5">
            <div class="col-12 ">
                <h2 class="text-center my-5">Pagina dei Contatti</h2>
            </div>
            <div class="col-12">
                <h5 class="text-center my-5">Informazioni di Contatto</h5>
                <div class="row">
                    <div class="col-12 col-md-6">
                        <div class="text-center">
                            <div class="my-2">
                                <strong>
                                    <i class="fas fa-map me-2<"></i>Indirizzo:
                                </strong>
                                    Via UnaViaQualsiasi,Num;città CAP
                            </div>
                            <div class="my-2">
                                <strong>
                                    <i class="fas fa-book me-2"></i>Partita Iva:
                                </strong>
                                    12345678901
                            </div>
                        </div>
                    </div>
                    <div class="col-12 col-md-6">
                        <div class="text-center ">
                            <div class="my-2">
                                <strong>
                                    <i class="fas fa-phone me-2<"></i>Telefono:
                                </strong>
                                    623 3733738
                            </div>
                            <div class="my-2">
                                <strong>
                                    <i class="fas fa-envelope me-2<"></i>Email:
                                </strong>
                                    info@Boolpress.com
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-12 my-5 write-on">
                    <h5 class="text-center">Scrivici</h5>
                    <form @submit="sendForm">
                        <div class="row">
                            <div class="row">
                                <div class="col-12 col-md-6 my-2">
                                    <label for="nome" class="control-label">Nome</label>
                                    <input type="text" class="form-control" name="nome" id="nome" placeholder="Nome" v-model="name">
                                </div>
                                <div class="col-12 col-md-6 my-2">
                                    <label for="cognome" class="control-label">Cognome</label>
                                    <input type="text" class="form-control" name="cognome" id="cognome" placeholder="Cognome" v-model="surname">
                                </div>
                                <div class="col-12 col-md-6 my-2">
                                    <label for="email" class="control-label">Email</label>
                                    <input type="mail" class="form-control" name="email" id="email" placeholder="Email" v-model="email">
                                </div>
                                <div class="col-12 col-md-6 my-2">
                                    <label for="telefono" class="control-label">Telefono</label>
                                    <input type="phone" class="form-control" name="telefono" id="telefono" placeholder="Telefono" v-model="phone">
                                </div>
                                <div class="col-12 my-2">
                                    <label class="control-label" for="messaggio">Messaggio</label>
                                    <textarea class="form-control" name="messaggio" id="messaggio" placeholder="Messaggio" v-model="message">
                                    </textarea>
                                </div>
                                <div class="col-12 my-2 text-center">
                                    <button type="submit" class="send_email">Invia</button>
                                </div>
                            </div>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
    .write-on{
        background-color: rgb(160, 116, 95);
        color: white;
        border-radius: 10px;
    }
     .send_email{
        background-color: white;
        color:rgb(160, 116, 95);
        border: none;
        padding: 10px 20px;
        transi

        &:hover{
            background-color: rgb(116, 84, 69);
            color: white;
        }
    }
</style>