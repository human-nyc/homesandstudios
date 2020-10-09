<template>
  <div class="footer">
    <a href="https://instagram.com/SocialStudiesworldwide" class="link" target="_blank">
      @SocialStudiesworldwide
    </a>
    <span class="copyright">
      © 2020 SOCIAL STUDIES Worldwide LLC.
    </span>
  </div>
</template>

<script>
export default {
}
</script>

<style lang="scss" scoped>
.footer {
  padding: var(--gutter);
  border-top: 1px solid;
  text-transform: uppercase;
  display: flex;
  justify-content: space-between;
  // @media (min-width: 1024px) {
  // }

  .link {
    display: inline;
    margin-right: 1em;
  }
  .copyright {
    display: inline;
    margin-right: 1em;
  }
}
</style>
