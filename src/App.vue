<template>
  <div>
    <h1>Welcome to Vue</h1>
    <div>Your message is {{ message }}</div>
    <div>Your message in uppercase: {{ message.toUpperCase() }}</div>
    <p>10 + 20 is {{ 10 + 20 }}</p>
    <p>
      {{ flag ? "YES" : "NO" }}
    </p>
    <div :id="divID">Sample div with attribute binding</div>

    <!-- Event Handling -->

    <button v-on:click="handleClick">Click Me</button>
    <p>
      <input type="text" :value="inputData" v-on:input="inputChanged($event)" />
      <br />
      Input data: {{ inputData }}
    </p>
    <p>
      Please enter your name: <input type="text" v-model="userName" />
      <br />
      The entered name is: {{ userName }}
    </p>
    <!-- Conditional Rendering -->
    <div>
      <h3>Conditional Rendering</h3>
      <p>
        <button @click="toggleParagraph">{{ btnText }}</button>
      </p>
      <p v-if="flag">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestias,
        impedit! Quibusdam accusantium hic, provident voluptate laboriosam amet
        fugit voluptatibus repellat animi ab inventore asperiores dolor tempora
        officiis odit, recusandae sint quae aliquid culpa. Aliquid quos unde cum
        id iusto accusamus fugiat magnam voluptatem. Eaque quia dolore officia
        voluptatum quo quisquam perspiciatis commodi voluptas, repellendus amet
        animi in veritatis laudantium id adipisci doloribus! Odit vero expedita
        sunt pariatur in unde explicabo sapiente dolores ipsam fugit nesciunt
        consectetur provident voluptatem perferendis, suscipit quisquam a veniam
        doloremque numquam aut debitis sint ut laboriosam. Eaque facere
        laboriosam debitis itaque odio iusto delectus quaerat voluptatibus.
      </p>
    </div>

    <!-- Rendering Lists -->

    <div>
      <h3>List of Actors</h3>
      <ul>
        <li v-for="actor in actorsList" :key="actor.name">
          Name: {{ actor.name }} City: {{ actor.city }}
        </li>
      </ul>
      <p>
        Name: <input type="text" v-model="newActor.name">
        <br>
        City: <input type="text" v-model="newActor.city">
        <br>
        <button @click="addActor" :disabled="addActorDisabled">Add Actor</button>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "Let us master Vue.js!!",
      flag: false,
      divID: "active",
      inputData: "Hello",
      userName: "",
      btnText: "Show Paragraph",
      actorsList: [
        {
          name: "Amitabh Bachhan",
          city: "Mumbai",
        },
        {
          name: "Ajeeth",
          city: "Chennai",
        },
        {
          name: "Aishwarya Rai",
          city: "Mumbai",
        },
        {
          name: "Deepika Padukone",
          city: "New Delhi",
        },
        {
          name: "Rajnikant",
          city: "Chennai",
        },
      ],
      newActor: {
        name: '',
        city: ''
      }
    };
  },
  methods: {
    handleClick() {
      alert("Button Clicked!!");
      document.querySelector("#active").style.fontWeight = "bold";
    },
    inputChanged(event) {
      // console.log(event.target.value);
      this.inputData = event.target.value;
    },
    toggleParagraph() {
      this.flag = !this.flag;
      this.btnText = this.flag ? "Hide Paragraph" : "Show Paragraph";
    },
    addActor() {
      this.actorsList.push(Object.assign({}, this.newActor));

      this.newActor.name = '';
      this.newActor.city = '';

      // this.newActor = {
      //   name: '',
      //   city: ''
      // };
    }
  },

  computed: {
    addActorDisabled() {
      return this.newActor.name === '' || this.newActor.city === '';
    }
  },

  mounted() {
    document.getElementById("active").style.color = "blue";
  },
};
</script>

<style>
h1 {
  color: red;
  text-align: center;
}
</style>