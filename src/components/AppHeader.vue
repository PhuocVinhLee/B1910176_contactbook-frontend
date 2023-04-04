<template>
    <nav class="navbar navbar-expand navbar-dark bg-dark">
        <a href="/" class="navbar-brand">Ứng dụng Quản lý danh bạ</a>
        <div class="mr-auto navbar-nav">
            <li class="nav-item">
                <router-link :to="{ name: 'contactbook' }" class="nav-link">
                    Danh bạ
                    <i class="fas fa-address-book"></i>
                </router-link>
            </li>
            <li class="nav-item" v-if="!IsChecked">
                <router-link :to="{ name: 'login' }" class="nav-link">
                    Đăng nhập
                    <i class="fas fa-address-book"></i>
                </router-link>
            </li>
            <li class="nav-item" v-if="IsChecked">
                <router-link :to="{ name: 'logout' }" class="nav-link">
                    Đăng xuất
                    <i class="fas fa-login"></i>
                </router-link>
            </li>
        </div>
    </nav>
</template>
<script>
 import { ref } from "vue";
export default{

    setup(){
        const IsChecked = ref(false);
        if(localStorage.getItem('token') == null){
            IsChecked.value = false;
        }
        else{
            IsChecked.value = true;
        }
        return{
            IsChecked,
        }
    }

}
</script>
    