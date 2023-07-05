---
layout: default
title: Search Results
permalink: /search-results/
---

<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<style>
  /* CSS for the loading screen */
  .loading-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(255, 255, 255, 0.8);
    z-index: 9999;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .loading-text {
    font-size: 24px;
    font-weight: bold;
  }
</style>
<script>
$(document).ready(function() {
  var urlParams = new URLSearchParams(window.location.search);
  var address = urlParams.get('address');
  var startDate = urlParams.get('start-date');
  var endDate = urlParams.get('end-date');

  // Construct the request payload
  var requestData = {
    address: address,
    start_date: startDate,
    end_date: endDate
  };

  // Show loading screen
  var loadingOverlay = $("<div>").addClass("loading-overlay");
  var loadingText = $("<div>").addClass("loading-text").text("Loading...");
  loadingOverlay.append(loadingText);
  $("body").append(loadingOverlay);

  // Make the API call with POST method and headers
  $.ajax({
    url: "http://localhost:5000/campsites",
    type: "POST",
    headers: {
      "Content-Type": "application/json",
      "Authorization": "Bearer your-token"
    },
    data: JSON.stringify(requestData),
    success: function(data) {
      var campsiteResults = $("#campsite-results");

      // Iterate over the campsite data and create HTML elements
      for (var i = 0; i < data.length; i++) {
        var campsite = data[i];
        var campsiteName = campsite[0];
        var campsiteDistance = campsite[1];

        // Create a <p> element to display the campsite name and distance
        var campsiteElement = $("<p>").text(campsiteName + " - " + campsiteDistance + " minutes away");

        // Append the <p> element to the campsite results container
        campsiteResults.append(campsiteElement);
      }

      // Hide loading screen
      loadingOverlay.remove();
    },
    error: function(xhr, status, error) {
      // Handle error response
      console.error(error);

      // Hide loading screen
      loadingOverlay.remove();
    }
  });
});
</script>


<h1>Search Results</h1>

<div id="campsite-results"></div>
