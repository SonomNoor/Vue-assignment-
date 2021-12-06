<!-- <template>
  <div>
    <b-table class ="info" if="posts && posts.length">
    <b-table   v-for="post of posts.slice(1,5)"  :key="post.title"> </b-table>
        <p><strong>{{post.title}}</strong></p>
        <p>{{post.body}}</p>

    </b-table>

    <b-table  class="table-info" v-if="errors && errors.length">
     <b-table   v-for="error of errors " :key="error.message"> </b-table>
        {{error.message}} </b-table>


  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {/*  */
    return {
      posts: [],
      errors: []
    }
  },

  // Fetches posts when the component is created.
  created() {
    axios.get(`http://jsonplaceholder.typicode.com/posts`)
    .then(response => {
      // JSON responses are automatically parsed.
      this.posts = response.data
    })
    .catch(e => {
      this.errors.push(e)
    })
  }
}
</script>
 */ -->


 <template>
    <div class="container">
        <h3 class="p-1 text-center">Vue.js - Display a list of items with v-for</h3>
        <table class="table table-striped table-bordered">
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Email</th>
                    <th>Role</th>
                    <th>Job</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user in users" :key="user.id">
                    <td>{{user.firstName}} {{user.lastName}}</td>
                    <td>{{user.email}}</td>
                    <td>{{user.role}}</td>
                    <td>{{user.job}}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    data() {
        return {
            users: [
                { firstName: 'Frank', lastName: 'Murphy', email: 'frank.murphy@test.com', role: 'User' , job:'police'},
                { firstName: 'Vic', lastName: 'Reynolds', email: 'vic.reynolds@test.com', role: 'Admin' },
                { firstName: 'Gina', lastName: 'Jabowski', email: 'gina.jabowski@test.com', role: 'Admin' },
                { firstName: 'Jessi', lastName: 'Glaser', email: 'jessi.glaser@test.com', role: 'User' },
                { firstName: 'Jay', lastName: 'Bilzerian', email: 'jay.bilzerian@test.com', role: 'User' },
                { firstName: 'Jay', lastName: 'Bilzerian', email: 'jay.bilzerian@test.com', role: 'User' }
            ]
        };
    }
};
</script>
