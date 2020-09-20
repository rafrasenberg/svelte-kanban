<script>
  export let websiteURL = "https://rafrasenberg.com";
  export let footerText = `Made with ♥ by Raf`;
</script>

<footer><a href="{websiteURL}" target="__blank">{footerText}</a></footer>

<style lang="scss">
  footer {
    position: absolute;
    width: 100%;
    font-size: 1rem;
    padding: 0.3rem 0;
    background-color: $black;
    color: $white;
    text-align: center;
    bottom: 0;
  }

  a {
    &:hover {
      color: $white;
    }
  }
</style>
