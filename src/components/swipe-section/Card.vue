<template>
  <div @mousedown="dragMouseDown" ref="card" class="card">
    <div class="card-says"></div>
    <img src="@/assets/person.jpg" alt srcset />
  </div>
</template>

<script>
export default {
  name: "Card",
  data() {
    return {
      positions: {
        clientX: undefined,
        movementX: 0,
        movementY: 0,
        degree: 0
      }
    };
  },
  methods: {
    dragMouseDown: function(event) {
      event.preventDefault();
      document.onmousemove = this.elementDrag;
      document.onmouseup = this.closeDragElement;
    },
    elementDrag: function(event) {
      const card_says = document.querySelector(".card-says");
      let dist;
      event.preventDefault();
      if (this.firstPosition == null) {
        this.firstPosition = this.$refs.card.offsetLeft;
      }
      this.$refs.card.classList.add("notransition");
      this.positions.movementX = this.positions.clientX - event.clientX;
      this.positions.clientX = event.clientX;
      this.$refs.card.style.left =
        this.$refs.card.offsetLeft - this.positions.movementX + "px";

      dist = (this.$refs.card.offsetLeft - this.firstPosition) / 30;
      this.positions.degree = dist;

      this.$refs.card.classList.remove("notransition");
      if (this.$refs.card.offsetLeft > this.firstPosition) {
        if (!(this.positions.degree > 15)) {
          this.$refs.card.style.webkitTransform =
            "rotate(" + this.positions.degree + "deg)";
          this.$refs.card.style.mozTransform =
            "rotate(" + this.positions.degree + "deg)";
          this.$refs.card.style.msTransform =
            "rotate(" + this.positions.degree + "deg)";
          this.$refs.card.style.oTransform =
            "rotate(" + this.positions.degree + "deg)";
          this.$refs.card.style.transform =
            "rotate(" + this.positions.degree + "deg)";
        }
        this.$refs.card.style.opacity = 1;
        this.$refs.card.style.opacity -= dist / 12;

        card_says.innerText = "LIKE";
        card_says.setAttribute(
          "style",
          "display: block; color: #00ff00; border: 5px solid #00ff00;"
        );
      } else {
        if (!(this.positions.degree > 15)) {
          this.$refs.card.style.webkitTransform =
            "rotate(" + this.positions.degree + "deg)";
          this.$refs.card.style.mozTransform =
            "rotate(" + this.positions.degree + "deg)";
          this.$refs.card.style.msTransform =
            "rotate(" + this.positions.degree + "deg)";
          this.$refs.card.style.oTransform =
            "rotate(" + this.positions.degree + "deg)";
          this.$refs.card.style.transform =
            "rotate(" + this.positions.degree + "deg)";
          this.$refs.card.style.opacity = 1;
          this.$refs.card.style.opacity -= -dist / 12;
        }

        card_says.innerText = "NOPE";
        card_says.setAttribute(
          "style",
          "display: block; color: red; border: 5px solid red;"
        );
      }
    },
    closeDragElement() {
      const card_says = document.querySelector(".card-says");
      if (this.$refs.card.offsetLeft >= this.firstPosition * 1.75) {
        this.$emit("judged", "like");
      } else if (this.$refs.card.offsetLeft <= this.firstPosition / 1.75) {
        this.$emit("judged", "dislike");
      }
      this.positions.clientX = undefined;
      this.positions.movementX = 0;
      this.positions.movementY = 0;
      this.$refs.card.style.left = this.firstPosition + "px";

      this.positions.degree = 0;
      this.$refs.card.style.webkitTransform =
        "rotate(" + this.positions.degree + "deg)";
      this.$refs.card.style.mozTransform =
        "rotate(" + this.positions.degree + "deg)";
      this.$refs.card.style.msTransform =
        "rotate(" + this.positions.degree + "deg)";
      this.$refs.card.style.oTransform =
        "rotate(" + this.positions.degree + "deg)";
      this.$refs.card.style.transform =
        "rotate(" + this.positions.degree + "deg)";
      this.$refs.card.style.opacity = 1;

      card_says.innerText = "";
      card_says.setAttribute("style", "display: none");
      document.onmouseup = null;
      document.onmousemove = null;
    },
    autoSwipe(event) {
      if (event == "liked") {
        const CARD = document.getElementsByClassName("card")[0];
        CARD.setAttribute("class", "card");

        CARD.style.transform = "rotate(" + 15 + "deg)";

        /*
        this.$refs.card.classList.remove("notransition");
        this.$refs.card.style.webkitTransform =
          "rotate(" + this.positions.degree + "deg)";
        this.$refs.card.style.mozTransform =
          "rotate(" + this.positions.degree + "deg)";
        this.$refs.card.style.msTransform =
          "rotate(" + this.positions.degree + "deg)";
        this.$refs.card.style.oTransform =
          "rotate(" + this.positions.degree + "deg)";
        this.$refs.card.style.transform = "rotate(" + this.positions.degree + "deg)";*/
      } else {
        console.log("nao");
      }
    }
  }
};
</script>
<style scoped>
.card {
  position: absolute;
  top: 12.5%;
  z-index: 9;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 70%;

  -webkit-transition: all 0.5s ease-in-out;
  -moz-transition: all 0.5s ease-in-out;
  -o-transition: all 0.5s ease-in-out;
  transition: all 0.5s ease-in-out;

  -webkit-touch-callout: none; /* iOS Safari */
  -webkit-user-select: none; /* Safari */
  -khtml-user-select: none; /* Konqueror HTML */
  -moz-user-select: none; /* Old versions of Firefox */
  -ms-user-select: none; /* Internet Explorer/Edge */
  user-select: none;
}
img {
  max-width: 100%;
  max-height: 100%;
  cursor: pointer;
}

.card-says {
  display: none;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-size: 5rem;
  position: absolute;
  top: 10px;
  left: 10px;
}

.notransition {
  -webkit-transition: none !important;
  -moz-transition: none !important;
  -o-transition: none !important;
  transition: none !important;
}
</style>
