<script>
  import '../styles.css'
</script>

<nav>
    <div class="navbar">
        <a href="/">Forside</a>

        <!-- Tall -->
        <div class="dropdown">
          <button class="dropbtn">Tall
            <i class="fa fa-caret-down"></i>
          </button>
          <div class="dropdown-content">
            <a href="/tall/oppg1">Oppgave 1</a>
            <a href="/tall/oppg2">Oppgave 2</a>
            <a href="/tall/oppg3">Oppgave 3</a>
          </div>
        </div>

        <!-- Algoritmer -->
        <div class="dropdown">
            <button class="dropbtn">Algoritmer
              <i class="fa fa-caret-down"></i>
            </button>
            <div class="dropdown-content">
              <a href="/algoritmer/oppg1">Oppgave 1</a>
              <a href="/algoritmer/oppg2">Oppgave 2</a>
            </div>
        </div>

        <!-- Strenger -->
        <div class="dropdown">
            <button class="dropbtn">Strenger
              <i class="fa fa-caret-down"></i>
            </button>
            <div class="dropdown-content">
                <a href="/strenger/oppg1">Oppgave 1</a>
                <a href="/strenger/oppg2">Oppgave 2</a>
                <a href="/strenger/oppg3">Oppgave 3</a>
                <a href="/strenger/oppg4">Oppgave 4</a>
            </div>
        </div>

        <!-- Klasser -->
        <div class="dropdown">
            <button class="dropbtn">Klasser
              <i class="fa fa-caret-down"></i>
            </button>
            <div class="dropdown-content">
                <a href="/klasser/oppg1">Oppgave 1</a>
                <a href="/klasser/oppg2">Oppgave 2</a>
                <a href="/klasser/oppg3">Oppgave 3</a>
                <a href="/klasser/oppg4">Oppgave 4</a>
            </div>
        </div>

        <!-- Data -->
        <div class="dropdown">
            <button class="dropbtn">Innhenting av data
              <i class="fa fa-caret-down"></i>
            </button>
            <div class="dropdown-content">
                <a href="/data/oppg1">Oppgave 1</a>
                <a href="/data/oppg2">Oppgave 2</a>
            </div>
          </div>

          <a href="/flag_quiz">Flag-Quiz</a>
      </div>  
</nav>

<slot></slot>

<style>
    /* Navbar container */
    .navbar {
    overflow: hidden;
    background-color: #413e3e;
    font-family: Arial;
    }

    /* Links inside the navbar */
    .navbar a {
    float: left;
    font-size: 16px;
    color: white;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
    }

    /* The dropdown container */
    .dropdown {
    float: left;
    overflow: hidden;
    }

    /* Dropdown button */
    .dropdown .dropbtn {
    font-size: 16px;
    border: none;
    outline: none;
    color: white;
    padding: 14px 16px;
    background-color: inherit;
    font-family: inherit; /* Important for vertical align on mobile phones */
    margin: 0; /* Important for vertical align on mobile phones */
    }

    /* Add a red background color to navbar links on hover */
    .navbar a:hover, .dropdown:hover .dropbtn {
    background-color: rgb(210, 177, 10);
    color: black;
    }

    /* Dropdown content (hidden by default) */
    .dropdown-content {
    display: none;
    position: absolute;
    background-color: #f9f9f9;
    min-width: 160px;
    box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
    z-index: 1;
    }

    /* Links inside the dropdown */
    .dropdown-content a {
    float: none;
    color: black;
    padding: 12px 16px;
    text-decoration: none;
    display: block;
    text-align: left;
    }

    /* Add a grey background color to dropdown links on hover */
    .dropdown-content a:hover {
    background-color: #ddd;
    }

    /* Show the dropdown menu on hover */
    .dropdown:hover .dropdown-content {
    display: block;
    } 
</style>