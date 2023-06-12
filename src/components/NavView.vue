<template>
  <nav>
    <input type="checkbox" id="check">
    <label for="check" class="checkbtn">
        <i class="fas fa-bars"></i>
    </label>
    <label class="logo">My Store</label>
    <ul>
        <li><a href="" class="active">Accueil</a></li>
        <li><a href="">Chaussures</a></li>
        <li><a href="">Maillot</a></li>
        <li><a href="">Equipements</a></li>
        <li><a href="">Contacts</a></li>
    </ul>
  </nav>
</template>

<script>

export default{
    name: 'NavView',
}
</script>

<style scoped>

@import '../assets/main.css';

</style>