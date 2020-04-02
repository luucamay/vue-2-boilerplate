<template>
  <v-layout>
    <v-card contextual-style="dark">
      <span slot="header">
        Posts
      </span>
      <div slot="body">
        <form @submit.prevent="crearPost(nuevoPost)">
          <div class="form-group">
            <div class="input-group">
              <div class="input-group-prepend">
                <span class="input-group-text">
                  <i class="fa fa-edit fa-fw"/>
                </span>
              </div>
              <input
                v-model="nuevoPost.tema"
                type="text"
                placeholder="Nombre del tema"
                class="form-control"
              >
            </div>
          </div>
          <div class="form-group">
            <div class="input-group">
              <div class="input-group-prepend">
                <span class="input-group-text">
                  <i class="fa fa-edit fa-fw"/>
                </span>
              </div>
              <input
                v-model="nuevoPost.mensaje"
                type="text"
                placeholder="Nuevo mensaje"
                class="form-control"
              >
            </div>
          </div>
          <div class="form-group">
            <button class="btn btn-outline-primary">
              Publicar Post
            </button>
          </div>
        </form>
      </div>
      <div slot="footer">
        <h5>publicados</h5>
        <div id="posts">
          <!-- reutilizando componente Post de Post.vue -->
          <v-post
            v-for="post in posts"
            :key="post.id"
            :tema="post.tema"
            :mensaje="post.mensaje"
          />
        </div>
      </div>
    </v-card>
  </v-layout>
</template>

<script>
import VLayout from '@/layouts/Default.vue';
import VPost from '@/components/Post.vue';
import VCard from '@/components/Card.vue';

export default {
  name: 'Posts',
  components: {
    VLayout,
    VPost,
    VCard,
  },

  data() {
    return {
      nuevoPost: {
        tema: '',
        mensaje: '',
      },
      posts: [],
    };
  },

  methods: {
    crearPost(nuevoPost) {
      const npost = {
        id: this.posts.length + 1,
        tema: nuevoPost.tema,
        mensaje: nuevoPost.mensaje,
      };
      this.posts.push(npost);
    },
  },
};
</script>
