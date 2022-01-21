<template>
   <div class="movie-wrapper">
        <div class="movie-frame" v-for="movie in movies" :key='movie.movieId'>
        <img class='portraits' :src="movie.movieImage" />

            <div>
                <div class="movie-info">
                    <span class='movie-span'>{{ movie.movieName }}</span>
                    <div>
                        <i class="fas fa-star movie-span"/><span class='movie-span'>{{ movie.movieRating }}</span>
                    </div>
                </div>
            </div>
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
  name: "Movies",

  data: function () {
    return {
      movies: [
        {
          movieId: 1,
          movieName: "Ace Ventura",
          movieImage: AceVentura,
          movieCategory: "Comédia",
        },
        {
          movieId: 2,
          movieName: "Atividade Paranormal",
          movieImage: AtivParanormal,
          movieCategory: "Terror",
        },
        {
          movieId: 3,
          movieName: "Avatar",
          movieImage: Avatar,
          movieCategory: "Aventura",
        },
        {
          movieId: 4,
          movieName: "Desejo de Matar",
          movieImage: DesejoDeMatar,
          movieCategory: "Ação",
        },
        {
          movieId: 5,
          movieName: "Doutor Sono",
          movieImage: DrSono,
          movieCategory: "Terror",
        },
        {
          movieId: 6,
          movieName: "Em Busca de Vingança",
          movieImage: Vinganca,
          movieCategory: "Ação",
        },
        {
          movieId: 7,
          movieName: "Jumanji: Bem-vindo à Selva",
          movieImage: Jumanji,
          movieCategory: "Aventura",
        },
        {
          movieId: 8,
          movieName: "Jurassic World: O Mundo dos Dinossauros",
          movieImage: Jurassic,
          movieCategory: "Aventura",
        },
        {
          movieId: 9,
          movieName: "Pânico 2",
          movieImage: Panico,
          movieCategory: "Terror",
        },
        {
          movieId: 10,
          movieName: "Seized",
          movieImage: Seized,
          movieCategory: "Ação",
        },
      ],
    };
  },
};
</script>

<style scoped>
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
    font-family: 'Poppins', sans-serif;
    color: #FBFBFB;
    padding: 0.5rem;
    line-height: 1.5rem;
}

.movie-wrapper {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2.75rem;
}
</style>