# Movie App

A web application that displays popular movies and allows users to search for movies using The Movie Database (TMDb) API.

## Description

The Movie App is a simple and interactive web application that provides a visually appealing interface for users to explore popular movies and search for specific titles. It utilizes The Movie Database (TMDb) API to fetch movie data including titles, poster images, ratings, and overviews.

## Features

- Displays a list of popular movies fetched from the TMDb API.
- Search functionality to find movies by title.
- Dynamic movie rating display with color-coded ratings (green for high, orange for medium, and red for low ratings).
- Responsive design for a seamless experience on both desktop and mobile devices.

## Installation

1. Clone the repository:

   git clone https://github.com/SuhasSindhuvadi/Movie-Application.git
   
2. Navigate to the project directory
   
   cd movie-app
   
3. Open index.html in your favorite web browser:

    
Usage
Open the app in your web browser.
The main page displays a list of popular movies.
Use the search bar at the top to find movies by title.
Hover over a movie to see its overview.
Code Overview
HTML Structure
The HTML file (index.html) contains the structure of the web page including the search form and a main section to display movies.

CSS Styling
The CSS file (style.css) includes styles for the movie cards, search bar, and overall layout to ensure a visually appealing design.

JavaScript Functionality
The JavaScript file (script.js) contains the logic to fetch and display movies, handle search functionality, and dynamically update the DOM.

Important URLs
API URL for Popular Movies: https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=YOUR_API_KEY&page=1
Image Path URL: https://image.tmdb.org/t/p/w1280
Search API URL: https://api.themoviedb.org/3/search/movie?api_key=YOUR_API_KEY&query="
Replace YOUR_API_KEY with your actual TMDb API key.

Example JavaScript Functions
Fetching Movies
javascript
Copy code
async function getMovies(url) {
    const res = await fetch(url);
    const data = await res.json();
    showMovies(data.results);
}
Displaying Movies
javascript
Copy code
function showMovies(movies) {
    main.innerHTML = '';
    movies.forEach((movie) => {
        const { title, poster_path, vote_average, overview } = movie;
        const movieEl = document.createElement('div');
        movieEl.classList.add('movie');
        movieEl.innerHTML = `
            <img src="${IMG_PATH + poster_path}" alt="${title}">
            <div class="movie-info">
                <h3>${title}</h3>
                <span class="${getClassByRate(vote_average)}">${vote_average}</span>
            </div>
            <div class="overview">
                <h3>Overview</h3>
                ${overview}
            </div>
        `;
        main.appendChild(movieEl);
    });
}
Handling Search
javascript
Copy code
form.addEventListener('submit', (e) => {
    e.preventDefault();
    const searchTerm = search.value;
    if (searchTerm && searchTerm !== '') {
        getMovies(SEARCH_API + searchTerm);
        search.value = '';
    } else {
        window.location.reload();
    }
});
Contributing
Contributions are welcome! Please follow these steps to contribute:

Fork the repository.

Create a new branch:

git checkout -b feature/your-feature-name
Make your changes and commit them:
git commit -m "Add some feature"
Push to the branch:
git push origin feature/your-feature-name
Open a pull request.
