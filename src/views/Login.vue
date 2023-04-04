<template>
    <form action="" @submit.prevent="handSubmit">
        <div class="text-center">
            <h3>Login</h3> <br>
            <div>
                <label class="text-end" for=""> Tài khoản: </label>
                <input v-model="email" type="email">
            </div>
            <br>
            <div> <label for=""> Mật khẩu: </label>
                <input v-model="password" type="text">
            </div>
            <div class="text-end"><input type="submit" value="Lưu" /></div>
        </div>

    </form>
</template>

<script>
import { ref } from "vue";
import axios from "axios"
import { useRouter } from "vue-router";
export default {
    setup() {
        const email = ref("");
        const password = ref("");
        const router = useRouter();
        async function handSubmit() {
            try {
                const response = await axios.post("http://localhost:3000/api/user/login", {
                    email: email.value,
                    password: password.value
                });
                console.log(response.data);
                if (response.data.message != null) {
                    alert(response.data.message);
                }
                else {
                    localStorage.setItem('token', response.data.token);
                    //console.log(localStorage.getItem('token'));
                    router.push("/");

                }

            } catch (e) {
                console.log(e);
            }
        }
        return {
            email, password, handSubmit,
        }
    }
}
</script>