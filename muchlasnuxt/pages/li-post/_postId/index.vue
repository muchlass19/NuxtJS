<template>
    <div>
        <nuxt-link :to="'/li-post'">
            <button class="btn btn-md btn-primary">Kembali</button>
        </nuxt-link>
        <nuxt-link :to="'/li-post/' + id + '/edit'">
            <button class="btn btn-md btn-warning">Ubah</button>
        </nuxt-link>
        <nuxt-link :to="'#'">
            <button class="btn btn-md btn-danger">Hapus</button>
        </nuxt-link>
        <h1>{{post.title}}</h1>
        <p>{{post.body}}</p>
        <p>User Id ={{post.userId}}</p>
    </div>
</template>

<script>
import Axios from 'axios'

export default {
    data(){
        return {
            post:{},
            id: this.$route.params.postId
        }
    },
    mounted(){
        Axios.get('http://localhost:3001/posts/' + this.$route.params.postId)
        .then((res) => {
            this.post = res.data || {}
        })
    }
}
</script>