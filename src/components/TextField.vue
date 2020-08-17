<script>
export default {
  props: [
    "placeholder",
    "type",
    "name",
    "id",
    "value",
    "label",
    "autocomplete",
    "readonly",
    "required",
    "autofocus"
  ],
  data() {
    return {
      focused: false
    };
  },
  computed: {
    localStyle() {
      return {
        borderColor: this.focused ? "rebeccapurple" : "#ccc"
      };
    },
    autosuggest() {
      if (this.autocomplete) {
        return "on";
      }
      return "off";
    }
  },
  methods: {
    change(e) {
      this.$emit("changed", e.target.value);
    },
    input(e) {
      this.$emit("change", e.target.value);
    },
    focus() {
      this.focused = true;
    },
    blur() {
      this.focused = false;
    }
  },
  render() {
    return (
      <label class="text-field">
        <span> {this.label}</span>
        <input
          placeholder={this.placeholder}
          type={this.type}
          name={this.name}
          id={this.id}
          value={this.value}
          style={this.localStyle}
          onChange={this.change}
          onInput={this.input}
          onFocus={this.focus}
          onBlur={this.blur}
          readonly={this.readonly}
          required={this.required}
          autocomplete={this.autosuggest}
          autofocus={this.autofocus}
        />
      </label>
    );
  }
};
</script>

<style scoped>
.text-field {
  position: relative;
  display: block;
  margin-bottom: 0;
}
.text-field input {
  outline: none;
  padding: 10px 10px;
  border: 1px solid #ddd;
}
.text-field input:focus {
  border-color: rebeccapurple;
}
</style>
