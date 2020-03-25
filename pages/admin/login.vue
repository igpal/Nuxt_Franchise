<template>

<v-content class="fill-height">
    <v-container
        fluid
    >
        <v-row
        align="center"
        justify="center"
        >
            <v-col
                cols="12"
                sm="8"
                md="4"
            >
                <v-card class="elevation-12">
                <v-toolbar
                    flat
                >
                    <v-toolbar-title>Войти в админку</v-toolbar-title>

                </v-toolbar>
                    <v-card-text>
                        <v-form 
                        ref="form"
                        :lazy-validation = true
                        @submit.prevent="loginToAdmin"
                        >
                        <v-text-field
                            v-model="login"
                            label="Логин"
                            name="login"
                            prepend-icon="person"
                            type="text"
                            :rules="loginRules"
                            required
                        />

                        <v-text-field class="md"
                            v-model="password"
                            id="password"
                            label="Пароль"
                            name="password"
                            prepend-icon="lock"
                            type="password"
                            :rules="passRules"
                            required
                        />
                        <div class="d-flex justify-end">
                            <v-btn 
                            color="blue-grey lighten-4" 
                            type="submit"
                            rounded
                            :loading = "loading"
                            >
                            Войти
                            </v-btn>
                        </div>
                        </v-form>
                    </v-card-text>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</v-content>
</template>

<script>
  export default {
      data: () => ({
        login:'',
        password:'',
        loading: false,
        passRules: [
        v => !!v || 'Пароль не должен быть пустым'
        ],
        loginRules: [
        v => !!v || 'Логин не должен быть пустым'
        ],
      }),
    layout: 'empty',

    mounted(){
        const {message} = this.$route.query;
        switch (message) {
        case 'login':
            alert('Для начала войдите в систему')
            break
        case 'logout':
            alert('Вы успешно вышли из системы')
            break
        case 'session':
            alert('Время сессии истекло, пожалуйста, зайдите заного')
            break
        }
    },

    methods:{
        loginToAdmin(){
        if (this.$refs.form.validate()) {
            try { 
                const formData = {
                    login: this.login,
                    password: this.password};

                     (async () => {
                        await this.$store.dispatch('auth/login',formData)
                        this.$router.push(`/admin`);
                    })() 
                    this.loading = false
            } catch (e) {
              this.loading = false;  
                }
            }
        }
    }
  }
</script>
<style scoped>
.form{
    width: 100%;
    padding-bottom: 4rem;
}
</style>