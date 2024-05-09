<template>
    <header class="header">
        <h1>TodoList</h1>
          <nav>
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </nav>
    </header>
</template>

<script>
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Header'
}
</script>

<style scoped>
    .header {
        background: #333;
        color: #fff;
        text-align: center;
        padding: 10px;
    }

    .header a {
        color: #fff;
        text-decoration: none;
        padding-right: 5px;
    }
</style>