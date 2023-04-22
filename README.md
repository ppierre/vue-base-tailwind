# Test de Menu basique

- Ajouter l'HTML du menu :
  ```html
  <button
    aria-controls="mainNav"
    aria-expanded="true"
    class="rounded-full border-2 border-red-600 bg-red-300 px-2"
  >
    menu
  </button>
  <!-- nav#mainNav>ul>li*3>a[href="#"]{item $} -->
  <nav id="mainNav">
    <ul>
      <li><a href="#">item 1</a></li>
      <li><a href="#">item 2</a></li>
      <li><a href="#">item 3</a></li>
    </ul>
  </nav>
  ```
- Recharger la page et tester avec [VueDevTools](https://devtools.vuejs.org/)
- Ajouter la définition de la [`ref`](https://vuejs.org/guide/essentials/reactivity-fundamentals.html#reactive-variables-with-ref) dans `<script setup>`
- L'utiliser avec [`v-show`](https://vuejs.org/guide/essentials/conditional.html#v-show) pour contrôler l'affichage du menu.
- Testez
- Mettre une [`Transition`](https://vuejs.org/guide/built-ins/transition.html#custom-transition-classes) au tour de la `<nav>` :
  ```html
  <Transition
    class="transition-transform duration-1000"
    enter-from-class="-translate-x-full"
    enter-to-class="translate-x-0"
    leave-active-class="-translate-x-full"
  ></Transition>
  ```
- Testez
