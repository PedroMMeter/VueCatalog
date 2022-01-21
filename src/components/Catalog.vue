<template>
  <div style="display: flex; flex-direction: row" @click="closeDropdown">
    <nav class="sidebar">
      <h1>MovieLog</h1>
      <input
        class="searchBar"
        type="text"
        placeholder="Pesquisar Filme"
        v-model="search"
      />
      <span
        class="tab"
        :class="{ activeTab: selectedTab === tab }"
        v-for="(tab, tabId) in tabs"
        :key="tabId"
        @click="selectedTab = tab"
      >
        {{ tab }}
      </span>
    </nav>
    <div class="container">
      <main>
        <div class="movie-wrapper">
          <div
            class="movie-frame"
            v-for="movie in filteredMovies"
            :key="movie.movieId"
            v-show="
              selectedTab === movie.movieCategory || selectedTab == 'Todos'
            "
          >
            <a :href="movie.movieRottenLink" target="_blank">
              <img class="portraits" :src="movie.movieImage" />
            </a>
            <div>
              <div class="movie-info">
                <span class="movie-span" style="margin-top: 0.4rem">{{
                  movie.movieName
                }}</span>
                <div class="movie-rate">
                  <fa
                    icon="star"
                    size="lg"
                    style="color: #fbfbfb; margin-top: 0.5rem"
                  />
                  <span class="movie-span">{{ movie.movieRating }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </main>
    </div>
  </div>
</template>

<script>
import AceVentura from "../assets/images/ace_ventura.jpg";
import AtivParanormal from "../assets/images/atividade_paranormal.jpg";
import Avatar from "../assets/images/avatar.jpg";
import DesejoDeMatar from "../assets/images/desejo_de_matar.jpg";
import DrSono from "../assets/images/doutor_sono.jpg";
import Vinganca from "../assets/images/em_busca_de_vinganca.jpg";
import Jumanji from "../assets/images/jumanji.jpg";
import Jurassic from "../assets/images/jurassic-world.jpg";
import Panico from "../assets/images/panico_dois.jpg";
import Seized from "../assets/images/seized.jpg";
export default {
  name: "Catalog",

  data: function () {
    return {
      movies: [
        {
          movieId: 1,
          movieName: "Ace Ventura",
          movieImage: AceVentura,
          movieCategory: "Comédia",
          movieRating: "3",
          movieRottenLink:
            "https://www.rottentomatoes.com/m/ace_ventura_pet_detective",
        },
        {
          movieId: 2,
          movieName: "Atividade Paranormal",
          movieImage: AtivParanormal,
          movieCategory: "Terror",
          movieRating: "3,5",
          movieRottenLink:
            "https://www.rottentomatoes.com/m/paranormal_activity",
        },
        {
          movieId: 3,
          movieName: "Avatar",
          movieImage: Avatar,
          movieCategory: "Aventura",
          movieRating: "4,5",
          movieRottenLink: "https://www.rottentomatoes.com/m/avatar",
        },
        {
          movieId: 4,
          movieName: "Desejo de Matar",
          movieImage: DesejoDeMatar,
          movieCategory: "Ação",
          movieRating: "2,5",
          movieRottenLink: "https://www.rottentomatoes.com/m/death_wish_2018",
        },
        {
          movieId: 5,
          movieName: "Doutor Sono",
          movieImage: DrSono,
          movieCategory: "Terror",
          movieRating: "4,5",
          movieRottenLink: "https://www.rottentomatoes.com/m/doctor_sleep",
        },
        {
          movieId: 6,
          movieName: "Em Busca de Vingança",
          movieImage: Vinganca,
          movieCategory: "Ação",
          movieRating: "2",
          movieRottenLink: "https://www.rottentomatoes.com/m/aftermath_2017",
        },
        {
          movieId: 7,
          movieName: "Jumanji: Bem-vindo à Selva",
          movieImage: Jumanji,
          movieCategory: "Aventura",
          movieRating: "4",
          movieRottenLink:
            "https://www.rottentomatoes.com/m/jumanji_welcome_to_the_jungle",
        },
        {
          movieId: 8,
          movieName: "Jurassic World: O Mundo dos Dinossauros",
          movieImage: Jurassic,
          movieCategory: "Aventura",
          movieRating: "4",
          movieRottenLink: "https://www.rottentomatoes.com/m/jurassic_world",
        },
        {
          movieId: 9,
          movieName: "Pânico 2",
          movieImage: Panico,
          movieCategory: "Terror",
          movieRating: "3,5",
          movieRottenLink: "https://www.rottentomatoes.com/m/scream_2",
        },
        {
          movieId: 10,
          movieName: "Seized",
          movieImage: Seized,
          movieCategory: "Ação",
          movieRating: "2",
          movieRottenLink: "https://www.rottentomatoes.com/m/seized_2020",
        },
      ],
      tabs: ["Todos", "Ação", "Aventura", "Comédia", "Terror"],
      selectedTab: "Todos",
      selectedMovie: 0,
      search: "",
      isOpen: false,
    };
  },
  computed: {
    filteredMovies: function () {
      return this.movies.filter((movie) => {
        return movie.movieName.toLowerCase().match(this.search.toLowerCase());
      });
    },
  },
};
</script>

<style scoped>
.dropdown-content {
  display: none;
}
.show {
  display: flex;
  flex-direction: column;
}
nav.sidebar {
  display: flex;
  flex-direction: column;

  align-items: center;

  max-width: 24rem;
  width: 100%;

  padding: 4rem 2rem;

  background: #232950;
  min-height: 100vh;
  max-height: 100%;
  margin-right: 2rem;
}
nav h1 {
  margin-bottom: 4rem;
  font-family: "Poppins", sans-serif;
  font-size: 3rem;
  font-weight: 600;
  color: rgb(201, 206, 179);
}
.searchBar {
  width: 15rem;
  height: 2.3rem;
  margin-bottom: 4rem;
  font-family: "Poppins", sans-serif;
  background-color: #ffffffe5;
  font-size: 1.3rem;
  border: none;
  border-radius: 0.3rem;
}
.tab {
  margin-bottom: 4.5rem;
  font-family: "Poppins", sans-serif;
  font-size: 2rem;
  font-weight: 600;
  color: rgb(247, 246, 242);
  cursor: pointer;

  transition: filter 0.2s;
}
.tab:hover {
  filter: brightness(0.8);
}
.activeTab {
  text-decoration: underline;
  color: rgb(247, 246, 242);
  cursor: default;
}
.movie-frame {
  position: relative;
  width: 15rem;
}
.portraits {
  position: relative;
  width: 14.31rem;
  height: 21.25rem;
}
.movie-info {
  display: flex;
  flex-direction: row;
  margin-bottom: 0.5rem;
  justify-content: center;
}
.movie-span {
  font-size: 1.5rem;
  font-family: "Poppins", sans-serif;
  color: #fbfbfb;
  padding: 0.5rem;
  line-height: 1.5rem;
}
.movie-rate {
  display: flex;
  flex-direction: row;
  margin-top: 0.5rem;
  padding: 0.5rem;
}
.movie-wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2.75rem;
}
</style>