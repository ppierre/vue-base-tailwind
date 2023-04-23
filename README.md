# Test d'interactions basiques

## Menu

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
- Tester, faire un commit
- Ajouter la définition de la [`ref`](https://vuejs.org/guide/essentials/reactivity-fundamentals.html#reactive-variables-with-ref) dans `<script setup>`

  ```js
  const menuIsOpen = ref(false)
  ```

- Recharger la page et tester avec [VueDevTools](https://devtools.vuejs.org/), faire un commit
- L'utiliser avec [`v-show`](https://vuejs.org/guide/essentials/conditional.html#v-show) pour contrôler l'affichage du menu.
- Testez avec VueDevTools, faire un commit
- Changer sa valeur au clic sur le bouton en lui en ajoutant :
  ```
  @pointerdown="menuIsOpen = !menuIsOpen"
  ```
- Testez, faire un commit
- Mettre une [`Transition`](https://vuejs.org/guide/built-ins/transition.html#custom-transition-classes) au tour de la `<nav>` :
  ```html
  <Transition
    class="transition-transform duration-1000"
    enter-from-class="-translate-x-full"
    enter-to-class="translate-x-0"
    leave-active-class="-translate-x-full"
  ></Transition>
  ```
- Testez, faire un commit

## Accordéon

- Faire le code HTML de l'accordéon :
  - `section*3>btn.text-xl{bouton $}+p>lorem`
- Testez, faire un commit
- Ajouter à `<script setup>` :
  ```js
  const sectionOpen = ref(1)
  ```
- Pour chaque section, ajouter et compléter dans l'HTML :
  ```html
  <section>
    <button class="text-xl" @click="/* change `sectionOpen` à 1 */">bouton 1</button>
    <p v-show="/* teste si `sectionOpen` est égale à 1 */">loren...</p>
  </section>
  ```
- Testez, faire un commit

## boucle sur des données

- Ajoutez dans `<script setup>` :
  ```js
  const sectionsData = [
    {
      label: 'bouton 1',
      texte: `texte panneau 1 Lorem ipsum dolor sit ame
      consectetur adipisicing elit. Inventore animi dolore,
      rerum magni laudantium quod excepturi laboriosam, 
      ex modi debitis harum reprehenderit eaque quam ut
      ea molestiae. Id, cum dolor!`
    },
    {
      label: 'bouton 2',
      texte: `texte panneau 2 Amet alias provident quos quis, 
      Officia ut ab dolores quos dolorem accusamus ad,
      consectetur unde minima, ipsum eligendi inventore id
      labore, laborum rerum laboriosam corrupti iste.
      Distinctio, perspiciatis!`
    },
    {
      label: 'bouton 3',
      texte: `texte panneau 3 Repudiandae corporis voluptates, 
      odit reprehenderit sint pariatur at voluptatum, cumque
      quia sit eligendi ex culpa eos, alias magnam molestiae
      id modi accusantium ipsa eveniet accusamus. Tempora 
      quis corporis et nam.`
    }
  ]
  ```
- Ajouter dans l'HTML ce code utilisant [`v-for`](https://vuejs.org/guide/essentials/list.html#v-for), pour tester :
  ```html
  <section v-for="({ label, texte }, key) of sectionsData" :v-key="key">
    <pre class="font-mono">key : {{ key }}</pre>
    <pre class="font-mono">label : {{ label }}</pre>
    <pre class="font-mono">texte : {{ texte }}</pre>
  </section>
  ```
- Testez, faire un commit
- Modifier le code de la section/boucle pour qu'il ait la même interaction (bouton, texte caché) que les accordéons précedant. Utiliser `key` à la place du nombre.
- Testez, faire un commit
