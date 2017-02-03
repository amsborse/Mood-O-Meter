# Mood-O-Meter
This project serves as an increment over the previous 'FeedMach' application that I, along with my team members, designed during the Persistent Technothon.

The project is built on these main APIs:
##1) Google Face API
An API which I've used to detect the prominent face in the image, and crop it out. I've also used this API to determine the smiling probability of the person in the image. You may find the github page here - https://github.com/googlesamples/android-vision

##2) Volley
Volley (https://github.com/mcxiaoke/android-volley) is a high-performance, asynchronous networking library that Google recently took over. It's robust architecture saves you from having to create tedious AsyncTasks. Also, it has pre-built support for JSON.

##3) ACRA
ACRA (https://github.com/ACRA/acra) is an excellent crash reporting API, which integrates seamlessly in the application, and lets you upload crash reports/exceptions/unusual behaviors in your application to your server as a form, json, and even supports crash reporting via e-mail.

##Project Flow:
1) User clicks 'Open Camera'

2) Camera click user's photo

3) Face is detected (if any), and is cropped. A toast is displayed, showing the smiling probability

4) On clicking one of the three emojis below, a POST network request is created, and a connection is established with the server

5) A pre-trained sentiment classification model (built on Caffe) is hosted up on our network. This takes an input of the image sent upstream, and returns the raw output via JSON

6) By overriding Volley's onResponseReceived(), we get the incoming JSON data, initialize an intent, load the received data as extras, and start the intent

7) The aforementioned intent links to another activity, which simply parses the output, and displays the final percentage