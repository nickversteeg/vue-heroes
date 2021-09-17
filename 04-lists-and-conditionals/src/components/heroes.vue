<template>
  <div class="content-container">
    <div class="section content-title-group">
      <h2 class="title">Heroes</h2>
    </div>
    <div class="columns">
      <div class="column is-3">
        <header class="card-header">
          <p class="card-header-title">heroes list</p>
        </header>
        <ul>
          <li
            v-for="hero in heroes"
            :key="hero.id"
            :class="{
              'is-active': selectedHero && hero.id === selectedHero.id,
            }"
          >
            <a @click="hero_onClick(hero)" class="list-item">
              <span>{{ hero.firstName }}</span>
            </a>
          </li>
        </ul>
      </div>
    </div>
    <div class="columns" v-if="selectedHero">
      <div class="column is-3">
        <header class="card-header">
          <p class="card-header-title">{{ selectedHero.firstName }}</p>
        </header>
        <div class="card-content">
          <div class="content">
            <div class="field">
              <label class="label" for="id">id</label>
              <label class="input" id="id" readonly>
                {{ selectedHero.id }}
              </label>
            </div>
            <div class="field">
              <label class="label" for="firstName">first name</label>
              <input
                class="input"
                id="firstName"
                v-model="selectedHero.firstName"
              />
            </div>
            <div class="field">
              <label for="show" class="checkbox">
                show more
                <input
                  type="checkbox"
                  id="show"
                  v-model="showMore"
                  class="is-primary"
                />
              </label>
            </div>
            <div class="field" v-show="showMore">
              <label class="label" for="lastName">last name</label>
              <input
                class="input"
                id="lastName"
                v-model="selectedHero.lastName"
              />
            </div>
            <div class="field" v-show="showMore">
              <label class="label" for="description">description</label>
              <input
                class="input"
                id="description"
                v-model="selectedHero.description"
              />
            </div>
          </div>
        </div>
      </div>
      <!-- <div class="column is-9">
        <table class="table is-fullwidth">
          <thead>
            <th>ID</th>
            <th>Name</th>
          </thead>
          <tbody>
            <tr
              v-for="hero in heroes"
              :key="hero.id"
              @mouseup="table_onMouseUp(hero)"
            >
              <td>{{ hero.id }}</td>
              <td>{{ hero.firstName }} {{ hero.lastName }}</td>
            </tr>
          </tbody>
        </table>
      </div> -->
    </div>
  </div>
</template>

<style>
li.is-active a {
  background-color: #48f;
}

.is-active a span {
  color: white;
}
</style>

<script>
export default {
  name: 'Heroes',
  data() {
    return {
      showMore: false,
      selectedHero: undefined,
      heroes: [
        {
          id: 10,
          firstName: 'Ella',
          lastName: 'Papa',
          description: 'fashionista',
        },
        {
          id: 20,
          firstName: 'Madelyn',
          lastName: 'Papa',
          description: 'the cat whisperer',
        },
        {
          id: 30,
          firstName: 'Haley',
          lastName: 'Papa',
          description: 'pen wielder',
        },
        {
          id: 40,
          firstName: 'Landon',
          lastName: 'Papa',
          description: 'arc trooper',
        },
      ],
    };
  },
  methods: {
    hero_onClick(hero) {
      this.selectedHero = hero;
    },
  },
};
</script>
