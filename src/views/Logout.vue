

<script>
import { ref } from "vue";
import axios from "axios"
import {useRouter} from "vue-router";
export default {

    setup() {
        const router = useRouter();
       localStorage.removeItem('token');
       router.push("/login");

        }
        //fgdg
    
}
</script>