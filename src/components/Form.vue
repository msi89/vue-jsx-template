<script>
import TextField from "./TextField";
export default {
  data() {
    return {
      form: {
        email: "",
        password: ""
      }
    };
  },
  methods: {
    handlerEmailChange(email) {
      this.form.email = email;
    },
    handlerSubmit(e) {
      e.preventDefault();
      alert("Form submitted");
      console.log("form data", this.form);
    },
    handlerPasswordChange(pwd) {
      this.form.password = pwd;
    }
  },
  render() {
    return (
      <div class="about">
        <form method="post" onSubmit={this.handlerSubmit}>
          <h1>This is an about page</h1>
          <label>Email address</label>
          <TextField
            type="email"
            id="email"
            name="email"
            value={this.form.email}
            onChange={this.handlerEmailChange}
            required={true}
          />
          <label>Password</label>
          <TextField
            type="password"
            id="password"
            name="password"
            value={this.form.password}
            onChange={this.handlerPasswordChange}
          />
          <button type="submit">Submit</button>
        </form>
      </div>
    );
  }
};
</script>

<style></style>