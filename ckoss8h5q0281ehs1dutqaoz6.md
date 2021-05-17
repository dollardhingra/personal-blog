## Another CoWIN Vaccine Availability Website

*Originally published at [dollardhingra.com](https://dollardhingra.com/blog/cowinquick-vaccine-availability/)
*
# Introduction
[CoWIN](https://www.cowin.gov.in/home) is a vaccination booking platform for booking vaccination for Indian citizens. This is the largest vaccination drive ever. Anyone can simple go and book the vaccination slots as per the availability in the respective state and districts. In this post I have created another platform just for checking the vaccine availability.
 

> But what's the need for creating a different platform for checking the availability when you already have the official platform?

# Problem
I had a hard time finding the vaccination slots (for 18-45 age group). Some of the problems I(and other people I think) faced:
* Most of the times the slots were not available and when they were available, they were booked in seconds. 
* The User experience of the original CoWIN portal is not that great. Firstly you need to login through your phone number(by an OTP which sometimes refuses to arrive on your phone). You are automatically logged out after 15-20 mins.
* There are some features that are missing, but can be really helpful in finding the slots. For eg: Ability to search across multiple districts.
* A filter for hiding the unavailable slots from the search result would have been really helpful.

> Some people have also written scripts for notifying whenever the slots are available. The idea is really great but there are couple of problems with the scripts approach:
As soon as you get the notification that slots are available in your district, you open up your browser ->login into the [CoWIN portal](https://www.cowin.gov.in/home) -> select the beneficiaries that you want to get vaccinated -> select the state & district/enter pin code and click search -> BOOM! the slots have already been booked! 
  

# Solution
I created a simple HTML page which calls the public CoWIN API in JS. Checkout the live demo [here](https://dollardhingra.com/cowinquick/).  
**Note:** This website can only be used for checking the available slots. For booking, the [official site](https://www.cowin.gov.in/home) must be used.

%[https://www.youtube.com/watch?v=knjqHZNs7LM]

This helps in booking as
* There is no need for entering phone number/otp again and again
* The results are visible for multiple districts at once.

# How I have booked more than 20 slots till now
I have booked more than 20 slots(for friends and family) with the following approach:
* There is usually a 1-2 hour window when the slots are open. Usually between 6-10pm on weekdays and 12-4pm on weekends. These timings may change so keep casually looking for the slots whenever you have your phone in hand through the [cowinquick site](https://dollardhingra.com/cowinquick/).

* Let's say that you find available slots in your district or a nearby district. Note the name of the center. Let's say that the name of the center is "BLK Hospital Site 1". 

* In one tab, login into the [cowin portal](https://www.cowin.gov.in/home) and select the city and distric/pin code. In the other tab you can open the [cowinquick site](https://dollardhingra.com/cowinquick/).

* Now check if "BLK Hospital Site 1" is available. If not, then come back to the [cowinquick site](https://dollardhingra.com/cowinquick/) and search again. There is high probability that "BLK Hospital Site 2" will come up next in few minutes. 

* Keep searching after every 5-10 seconds. There is a chance that you are searching in the time window where the slots are being updated. You will come to know that the slots are being updated if you keep searching for 5-10 mins(clicking search after every 10-20 seconds). Either of following will happen:
    - You will see that for some centers the slots are being open and booked in 15-20 seconds. Try booking that center in those 15 seconds. The advantage you have on [cowinquick site](https://dollardhingra.com/cowinquick/) is that you can see the results for multiple districts at once & you don't need to select 18+ again on every search. 

    - There maybe a situation when you don't see any centers updating slots. You can then try the same after some time. 



# Help Needed
Currently the JS code is written by me. I also copied the code from different JS snippets. There is a need of refactoring needed by some good JS developer(I don't know JS!! I am a python dev). Also, I have opened some issues(enhancements) in the github repo on which work can be done. 
> If you are passionate about open source contribution then please free to contribute! I will include your name in the list of contributors. The code can be found [here](https://github.com/dollardhingra/cowinquick)