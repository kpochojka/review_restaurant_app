# Restaurant Review App
Project 7 by Frontend Path by Openclassrooms.com - an web app with Google API

Requirements:
1. A Google Maps map loaded with the Google Maps API.
2. A list of restaurants on the right side of the page that are within the area displayed on the map.
3. Add a review about an existing restaurant.
4. Add a restaurant by clicking on a specific place on the map.

Technologies: HTML5, CSS3, Flexbox, jQuery, Javascript, Google API.

to visit the page click link below:
https://kpochojka.github.io/review_restaurant_app/


# Code Example

//display information when the restaurant is clicked

            function displayRestaurantInfo(place) {
                $('#review-window').show();
                $('#add-review-button').show();
                restaurantInfoDiv.show();
                $('#name').text(place.name);
                $('#address').text(place.vicinity);
                $('#telephone').text(place.formatted_phone_number);

                let reviewsDiv = $('#reviews');
                let reviewHTML = '';
                reviewsDiv.html(reviewHTML);
                if (place.reviews) {
                    if (place.reviews.length > 0) {
                        for (let i = 0; i < place.reviews.length; i += 1) {
                            let review = place.reviews[i];
                            let avatar;
                            if (place.reviews[i].profile_photo_url) {
                                avatar = place.reviews[i].profile_photo_url;
                            } else {
                                avatar = 'image/rest.png';
                            }
                            reviewHTML += `<div class="restaurant-reviews">
                                          <h3 class="review-title">
                                             <span class="profile-photo" style="background-image: url('${avatar}')"></span>`;
                            if (place.rating) {
                                reviewHTML += `<span id="review-rating" class="rating">${placeRating(review)}</span>`;
                            }
                            reviewHTML += ` <h3>${place.reviews[i].author_name}</h3>
                                    </h3>
                                                <p> ${place.reviews[i].text} </p>
                                            </div>`;
                            reviewsDiv.html(reviewHTML);
                        }
                    }
                }
