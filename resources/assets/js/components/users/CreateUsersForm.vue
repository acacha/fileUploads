<template>
    <div id="create-users-form">
        <form @submit.prevent="submit">
            <div class="box-body">
                <div class="form-group">
                    <label for="name">Name: </label>
                    <input type="text" name="name" id="name" placeholder="Name" value="" v-model="name">
                </div>
                <div class="form-group">
                    <label for="email">Email: </label>
                    <input type="email" name="email" id="email" placeholder="Email" value="" v-model="email">
                </div>
                <div class="form-group">
                    <label for="password">Password: </label>
                    <input type="password" name="password" id="password" placeholder="Password" value="" v-model="password">
                </div>
                <div class="form-group">
                    <label for="file">File: </label>
                    <input type="file" name="file" id="file" value="">
                </div>

                <button type="submit" id="create-user-button" class="btn btn-primary">Create</button>

            </div>


        </form>
    </div>
</template>

<script>

    export default {
      mounted() {
          console.log('Component mounted.')
      },
      data() {
        return {
          name: '',
          email: '',
          password: ''
        }
      },
      methods: {
        submit() {
          var data = new FormData();
          data.append('name',this.name)
          data.append('email',this.email)
          data.append('password',this.password)
          data.append('file', document.getElementById('file').files[0]);
          window.axios.post('/api/v1/user', data)
            .then(function (response) {
              console.log(response);
            })
            .catch(function (error) {
              console.log(error);
            });
        }
      }
    }
</script>
