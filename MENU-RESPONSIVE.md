# Responsive collapsible menu

1. Create the following files with basic html structure with js and css attached:

```
index.html
js/script.js
css/style.css
```

2.a Add accessible html navigation and menu.

```
  <nav class='nav-top-level closed' id='main-nav' aria-label="Main navigation" role="navigation">
    ...
    <ul id="menu-items">
      <li><a href="#home">Home</a></li>
      <li><a href="#products">Products</a></li>
      <li><a href="#about">About Us</a></li>
    </ul>
  </nav>
```

2.b Style the menu in CSS file

```
.nav-top-level a {
  color: #f2f2f2;
  padding: 1em;
  text-decoration: none;
  font-size: 1em;
}

.nav-top-level a:hover,
.nav-top-level a:focus {
  background-color: #ddd;
  color: #000;
}

.nav-top-level ul {
  list-style: none;
  background-color: #333;
  padding-left: 0;
}

.nav-top-level ul li {
  margin-left: 0;
}
```

3.a Add the actual toggele button to the same navigation:

```
  <nav class='nav-top-level closed' id='main-nav' aria-label="Main navigation" role="navigation">
    <button id="menu-top-button" class="menu-toggle" aria-expanded="false" aria-controls="menu-items">
      <span class="bar"></span>
      <span class="bar"></span>
    </button>
    ...
  </nav>
```

3.b. Style close toggle button

```
.bar {
  display: block;
  width: 25px;
  height: 5px;
  margin: 5px 0;
  background-color: #000;
}
```

3.c. Add JavaScript code to exacute toggle.

Add toggle menu function and getting navigation and `aria-expanded` attribute of the target.

```
function toggleMenu(event) {

  var navBar = document.getElementById("main-nav");
  var expanded = event.currentTarget.getAttribute("aria-expanded");

}
```

Add classes to navbar when expanded and populate `else` section for the opposite effect.

```
  if (expanded === "true") {
    navBar.classList.add("closed");
    navBar.classList.remove("opened");
    event.currentTarget.setAttribute('aria-expanded', 'false');
  } else {
    ...
  }
```

Outside of the function, add event lister for click on `menu-top-button` element.

```
// Add event listener for clicking top menu button.
document.getElementById('menu-top-button').addEventListener('click', toggleMenu, false);

```

3.d. Add styling for `opened` and `closed`

```
.opened ul {
  display: block;
  position: absolute;
  z-index: 1;
  width: 75%;
}

.closed ul {
  display: none;
}

.nav-top-level.opened a {
  display: block;
  text-align: left;
}

.opened .bar {
  background-color: #999;
}
```

3.e. Add CSS animation.

```
.bar {
  ...
  
  /* Animation */
  transition: all .3s ease;
}

.opened .bar:nth-child(1) {
  transform: translateY(8px) rotate(45deg);
}

.opened .bar:nth-child(2) {
  transform: translateY(-2px) rotate(-45deg);
}
```
