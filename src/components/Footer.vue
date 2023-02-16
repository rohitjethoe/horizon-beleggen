<template>
  <footer>
    <a href="https://rohit.nl" target="_blank">
        Made with <span class="text-gradient">❤</span> by Rohit 
    </a>
  </footer>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
    footer {
        background-color: #27332F;
        padding: 4px;
        text-align: center;
        a:link, a:visited {
            color: #fff;
            text-decoration: none;
            font-size: 20px;
            .text-gradient {  
                background-image: var(--accent-gradient);
                background-clip: text;
                -webkit-background-clip: text;
                -webkit-text-fill-color: transparent;
                background-size: 400%;
                background-position: 0%;
            }
        }
    }
</style>