---
layout: default
title: Use world map on Grafana
parent: Grafana
nav_order: 1
---

# Use world map to display user activity

Based on Elastic Search info, I created a dashboard to display a map where we can see user connections.

# How

I had to analyse the content of the access logs to identify the user's info about location.
After that, i had to identify to which app the user try to access and create a filter based on the referrer url.

# Complexity

There are lot of field based on the request, the response,... the difficulties was to retrieve the good ones to get the location and the right filters to display the right information

# Result

[![Grafana world map result](https://user-images.githubusercontent.com/1218742/164321728-8b99705a-6bbd-4a36-ab26-22c11c962623.png)](https://user-images.githubusercontent.com/1218742/164321137-f8ead2fb-d311-4a07-b90b-692b1d95edce.mp4 "Grafana world map result")

<div align="center">click on the image to see the video</div>
