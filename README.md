<pre>
# groupProject1

 Date Picker:
 http://t1m0n.name/air-datepicker/docs/
 
 JS Animation
 https://www.javascripting.com/animation/
 https://www.javascripting.com/view/howler-js

  
APIs (tentative)
https://www.openbrewerydb.org, 
 https://www.calendarindex.com /
   https://holidayapi.com
  
Code Dump 
<!--date picker-->
 
    head 
        link href="dist/css/datepicker.min.css" rel="stylesheet" type="text/css" 
        script src="dist/js/datepicker.min.js"  /script 
  
        <!-- Include English language --> 
        script src="dist/js/i18n/datepicker.en.js"  /script 
    /head 
 
    input type='text' class="datepicker-here" data-position="right top" / 
 
    //manual Initialization 
$('#my-element').datepicker([options]) 
// Access instance of plugin 
$('#my-element').data('datepicker') 
 
Permanently visible calendar 
div class="datepicker-here" data-language='en'          /div  



<!--if no holidays that day, take username and declare "its USERNAME DAY"-->
 
if (holiday == false{ get USERNAME, "its USERNAME DAY});
 
<!---standard AJAX code, from Unit 6.11, BANDS IN TOWN exercise-->
 
script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"  
script 
  function searchBandsInTown(artist) { 
 
    // Querying the bandsintown api for the selected artist, the ?app_id parameter is required, but can equal anything 
    var queryURL = "https://rest.bandsintown.com/artists/" + artist + "?app_id=codingbootcamp"; 
    $.ajax({ 
      url: queryURL, 
      method: "GET" 
    }).then(function(response) { 
 
      // Printing the entire object to console 
      console.log(response); 
 
      // Constructing HTML containing the artist information 
      var artistName = $("<h1>").text(response.name); 
      var artistURL = $("<a>").attr("href", response.url).append(artistName); 
      var artistImage = $("<img>").attr("src", response.thumb_url); 
      var trackerCount = $("<h2>").text(response.tracker_count + " fans tracking this artist"); 
      var upcomingEvents = $("<h2>").text(response.upcoming_event_count + " upcoming events");
      var goToArtist = $("<a>").attr("href", response.url).text("See Tour Dates");

      // Empty the contents of the artist-div, append the new artist content
      $("#artist-div").empty();
      $("#artist-div").append(artistURL, artistImage, trackerCount, upcomingEvents, goToArtist);
    });
  }

  // Event handler for user clicking the select-artist button
  $("#select-artist").on("click", function(event) {
    // Preventing the button from trying to submit the form
    event.preventDefault();
    // Storing the artist name
    var inputArtist = $("#artist-input").val().trim();

    // Running the searchBandsInTown function (passing in the artist as an argument)
    searchBandsInTown(inputArtist);
  });
/script
</pre>