<template>
    <div>
        <nuxt-link :to="'/li-post'">
            <button class="btn btn-md btn-primary">Kembali</button>
        </nuxt-link>

        <h1>Buat List Post Baru</h1>
        <form>
            <input type="text" name="title" v-model="post.title" placeholder="Masukkan Judul">
            <input type="text" name="body" v-model="post.body" placeholder="Masukkan Isi Post">
            <input type="number" name="userId" v-model="post.userId" placeholder="Diisi hanya dengan angka">
            <button class="btn btn-md btn-success" @click.prevent="simpan">Simpan</button>
        </form>
    </div>
</template>

<script>
import Axios from 'axios'

export default {
    data(){
        return{
            post:{}
        }
    },
    methods:{
        simpan(){
            Axios.post('http://localhost:3001/posts', this.post)
            .then((send) =>{
                this.$router.push('/li-post')
            })
        }
    }
}
</script>