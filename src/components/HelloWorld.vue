<template>
<div class="buttons">
<button class="duplicate">Duplicate</button>
  
<button class="changeHeading">Change Heading</button>

<button id="deleteInstance">Delete Last Instance</button>
  
<button data-toggle-btn>Toggle Details</button>
</div>

<div class="wrapper">
  <div class="container">
  <img class="image" src="https://mcdn.wallpapersafari.com/medium/71/81/0VgmpU.jpg"/>
  <div class="header">
    <h1>My Card: Mario</h1>
    </div>
  
<details class="details">
<summary>Details</summary>
<div class="desc-txt">
    <p>My card is displaying one of my favorite video game characters ever, Mario. I chose this character because it is a character that means a lot to me through my life. This card design has the title at the top, displayed in the top-center of the card, with a photo beneath it. The photo itself displays mario jumping upwards, with a light blue background that contrasts well with the rest of the card.</p>
    </div>
    </details>
</div>
</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted() {
const details = document.querySelector('summary');

document.querySelector('button[data-toggle-btn]').addEventListener('click', (e) => {
  if (details.parentNode.getAttribute('open')) {
    details.parentNode.removeAttribute('open');
  }
  else {
    details.parentNode.setAttribute('open','open');    
  }
});

document.querySelector('.duplicate').addEventListener('click', function(e) {
  const itemToClone = document.querySelector('.wrapper').cloneNode(true);
  document.body.appendChild(itemToClone);
});

document.querySelector('.changeHeading').addEventListener('click', function(e) {
  let name = prompt("Rename Title: ");
  if (name) {
    document.querySelector('.wrapper h1').innerText = name;
  }
});

document.querySelector('#deleteInstance').addEventListener('click', function(e) {
  let wantsTo = confirm("Are you sure?");
  if (wantsTo) {
    if (document.querySelector('.wrapper:last-child') !== document.querySelector('.wrapper')) {
      document.querySelector('.wrapper:last-child').remove();      
    }
    else {
      alert("You Cannot Delete With 1 Card Left!");
    }
  }
});
  }
}
</script>

<style scoped>
.wrapper {
  width: 400px;
  border: 2px solid black;
  display: inline-flex;
  height: 600px;
}

.image {
  width: 400px;
}

.header {
  text-align: center;
  font-weight: bold;
  font-size: 1rem;
}

.buttons button:focus,
.buttons button:hover {
  background-color: CornflowerBlue;
}

.buttons button:active {
  background-color: CornflowerBlue;
}

button {
  padding: 6px;
  font-size: 16px;
}

details {
  padding: 10px;
}

.details summary {
  font-size: 20px;
  font-weight: bold;
}

@media only screen and (max-width: 1200px){
  .wrapper {
    background-color: pink;
  }
}

@media only screen and (max-width: 600px){
  .wrapper {
    background-color: blue;
  }
}

@media only screen and (max-width: 425px){
  .wrapper {
    font-weight: normal;
  }
  .wrapper .header h3 {
    font-size: 12px;
  }
  .wrapper .header h4 {
    font-size: 10px !important;
  }
  details {
    display: none;
  }
}
</style>