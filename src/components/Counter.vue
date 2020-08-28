<template>
  <div style="background-color: black">
    <v-button @click="randomStart()" class="btn">
      <img
        src="https://phoneky.co.uk/thumbs/screensavers/down/abstract/stopbutton_3fum9fwb.gif"
        height="50px"
        class="rounded-pill"
      />
    </v-button>
    <br />
    <button v-bind:disabled="end" @click="randomDamage()" class="btn btn-info">Attack{{Label}}</button>
    <button
      v-bind:disabled="end"
      @click="randomSpDamage()"
      class="btn btn-info"
    >Special Attack{{Label}}</button>
    <div class="row text-danger">
      <div class="col-sm text-danger">
        <p>{{randomPlayer}}</p>
        <p>HP : {{hp1}}</p>
        <p>
          <img v-bind:style="{width : hp1 + 'px'}" :src="healthbar" alt height="20px" />
        </p>
        <img :src="imagePlayer" :height="hp1" />
      </div>
      <div class="col-sm text-danger">
        <h1 v-if="hp1 <= 0 & hp2 <=0">
          <br />
          <img
            src="https://cdn.discordapp.com/attachments/392353546332405763/748200974153154640/235-2359549_street-fighter-ko-png-ko-street-fighter-png.png"
          />
          DRAW!
        </h1>
        <h1 v-else-if="hp2 <= 0 ">
          <br />
          <img
            src="https://cdn.discordapp.com/attachments/392353546332405763/748200974153154640/235-2359549_street-fighter-ko-png-ko-street-fighter-png.png"
          />
          {{randomPlayer}} WIN
        </h1>
        <h1 v-else-if="hp1 <= 0 ">
          <br />
          <img
            src="https://cdn.discordapp.com/attachments/392353546332405763/748200974153154640/235-2359549_street-fighter-ko-png-ko-street-fighter-png.png"
          />
          {{randomMonster}} WIN
        </h1>
        <br />
        <br />
        <br />
        <p v-if="hp1!=0 & hp2!=0">
          <img
            src="https://www.pngmart.com/files/11/Versus-Battle-Transparent-PNG.png"
            height="300px"
          />
        </p>
      </div>

      <div class="col-sm text-danger">
        <p>{{randomMonster}}</p>
        <p>HP : {{hp2}}</p>
        <p>
          <img v-bind:style="{width: hp2 + 'px'}" :src="healthbar" alt height="20px" />
        </p>
        <img :src="imageMonster" :height="hp2" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      randomPlayer: "",
      randomMonster: "",
      imagePlayer: "",
      imageMonster: "",
      hp1: "1",
      hp2: "1",
      end: true,
      healthbar:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",
      player: [
        {
          name: "Thor",
          hp: 380,
          image1:
            "https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/02ad5b68-d8e9-4bc6-9936-fdd4c662840d/d5fivwn-89d4a632-6653-4484-8e41-36c1ab5f19fb.gif?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOiIsImlzcyI6InVybjphcHA6Iiwib2JqIjpbW3sicGF0aCI6IlwvZlwvMDJhZDViNjgtZDhlOS00YmM2LTk5MzYtZmRkNGM2NjI4NDBkXC9kNWZpdnduLTg5ZDRhNjMyLTY2NTMtNDQ4NC04ZTQxLTM2YzFhYjVmMTlmYi5naWYifV1dLCJhdWQiOlsidXJuOnNlcnZpY2U6ZmlsZS5kb3dubG9hZCJdfQ.ol4Rnm3DYhjHmsjDyn-haajEbto75qJEZZqGaJo02C8",
        },
        {
          name: "Spiderman",
          hp: 360,
          image1:
            "https://lh3.googleusercontent.com/proxy/_2niyitU4WQ5yH9NOc7HXy4PCCjTO6V9UlVI-aPAHm3vhHkuQwUL5p7py3IDj70hbYfn1ZruK7Kyd15aEvC-ieab",
        },

        {
          name: "Super man",
          hp: 350,
          image1:
            "https://static.wixstatic.com/media/b0863f_cd50e1876d4143d8b71ae5fe6bbcd9b5.gif",
        },
        {
          name: "Deadpool",
          hp: 360,
          image1:
            "https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/i/4a152979-6d77-49ac-ad8b-9e91a2c45b88/d1vaj1h-4510d3c2-5d69-4de3-aac8-587d76604a0e.gif",
        },
      ],
      monster: [
        {
          name: "Akuma",
          hp: 430,
          image1:
            "https://www.fightersgeneration.com/characters/akuma-c-combo.gif",
        },
        {
          name: "Dhalsim",
          hp: 420,
          image1:
            "https://www.fightersgeneration.com/nf/char/gif/dhalsim/dhalsim-sfa3-air-twirl-kick.gif",
        },
        {
          name: "Venom",
          hp: 400,
          image1:
            "https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/88db413b-b2db-4198-b1f1-30651b585c22/d5db4d3-4d1cc4cb-dd8d-4fbc-9d04-16ae2f70e349.gif?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOiIsImlzcyI6InVybjphcHA6Iiwib2JqIjpbW3sicGF0aCI6IlwvZlwvODhkYjQxM2ItYjJkYi00MTk4LWIxZjEtMzA2NTFiNTg1YzIyXC9kNWRiNGQzLTRkMWNjNGNiLWRkOGQtNGZiYy05ZDA0LTE2YWUyZjcwZTM0OS5naWYifV1dLCJhdWQiOlsidXJuOnNlcnZpY2U6ZmlsZS5kb3dubG9hZCJdfQ.RxNrpax7vWsDrIxp9z5g9h-sYE-gVzQb-H7u3rN9reA",
        },
        {
          name: "Thanos",
          hp: 410,
          image1:
            "https://thumbs.gfycat.com/BrokenSerpentineAfricanbushviper-size_restricted.gif",
        },
      ],
    };
  },
  props: {
    Label: String,
  },
  methods: {
    randomStart: function () {
      this.chosenNumber1 = Math.floor(Math.random() * this.player.length);
      this.randomPlayer = this.player[this.chosenNumber1].name;
      this.hp1 = this.player[this.chosenNumber1].hp;
      this.imagePlayer = this.player[this.chosenNumber1].image1;
      this.chosenNumber2 = Math.floor(Math.random() * this.monster.length);
      this.randomMonster = this.monster[this.chosenNumber2].name;
      this.hp2 = this.monster[this.chosenNumber2].hp;
      this.imageMonster = this.monster[this.chosenNumber2].image1;
      this.end = false;
    },
    randomDamage: function () {
      this.randomPlayerAttack = Math.max(Math.floor(Math.random() * 10) + 1, 3);
      this.hp2 -= this.randomPlayerAttack;
      this.imagePlayer = this.player[this.chosenNumber1].image1;
      this.randomMonsterAttack = Math.max(
        Math.floor(Math.random() * 15) + 1,
        5
      );
      this.hp1 -= this.randomMonsterAttack;
      this.imageMonster = this.monster[this.chosenNumber2].image1;
      if ((this.hp1 <= 0) & (this.hp2 <= 0)) {
        this.hp1 = 0;
        this.hp2 = 0;
        this.end = true;
      } else if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.end = true;
        this.imageMonster = this.monster[this.chosenNumber2].image1;
      } else if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.end = true;
        this.imagePlayer = this.player[this.chosenNumber1].image1;
      }
    },
    randomSpDamage: function () {
      this.randomPlayerAttack = Math.max(
        Math.floor(Math.random() * 20) + 1,
        10
      );
      this.hp2 -= this.randomPlayerAttack;
      this.imagePlayer = this.player[this.chosenNumber1].image1;
      this.randomMonsterAttack = Math.max(
        Math.floor(Math.random() * 15) + 1,
        5
      );
      this.hp1 -= this.randomMonsterAttack;
      this.imageMonster = this.monster[this.chosenNumber2].image1;
      if ((this.hp1 <= 0) & (this.hp2 <= 0)) {
        this.hp1 = 0;
        this.hp2 = 0;
        this.end = true;
      } else if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.end = true;
        this.imageMonster = this.monster[this.chosenNumber2].image1;
      } else if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.end = true;
        this.imagePlayer = this.player[this.chosenNumber1].image1;
      }
    },
  },
};
</script>

<style>
</style>