---
title: A Route Optimisation Challenge - Inter IIT Tech Meet 2019.
tags: [Competition, Algorithms, Tabu Search, Greedy]
style: fill
color: primary
description: My team came 6th among all the IIT that participated and we got joint silver for our approach
external_url: 
---

I had a chance to partcipate in one of the challenges in Inter IIT tech meet which is conducted every year pan India where teams from all IITs partcipate. It was a cold December month in 2019 where most of people from college had went back home for winter vacation, while some of us stayed back to complete these competitions.

So the problem statement was given to us by BOSCH company(A German MnC) which involved a particular set of points in Bangalore city from which people need to be boarded on buses. These points were to be traversed by buses from starting point covering all the mentioned points in dataset mutually exclusively, with the constraint of minimum and maximum occupancy for passengers and within a given time window.

Our approach to solve this problem on minimising operating cost was based on kind of greedy approach in O(n<sup>3</sup>)
The solution was as follows:

The dataset that was given to be worked upon is shown below:
{% gist e51bc7cc576026dc120e80a57a53e0ec data.py %}

1. Generate distance time matrix using API which takes in longitudes and latitudes.
2. Sort the points according to the angle they make from the vertical.
{% gist e51bc7cc576026dc120e80a57a53e0ec sort.py %}

3. Generate a solution satifying the first constraint of atleast 85% of bus should be filled.
{% gist e51bc7cc576026dc120e80a57a53e0ec initial_route.py %}

4. Now we have the occupancy list modified by removing the onboarded passengers already from capacity.
5. It's time to swap nodes within individual routes generated to minimise time taken fro travelling through the route, this is also known as intra node swapping in vehicle routing problem. For more info. read this article [Vehicle Routing Problem](https://ameerd.github.io/files/VRP-Project---Github-Version.html)
{% gist e51bc7cc576026dc120e80a57a53e0ec swap.py %}
{% gist e51bc7cc576026dc120e80a57a53e0ec intra_node_swapped_route.py %}

6. Using the above swap functions we swap nodes amongst all the possible routes individually. Post this we are going to use standard optimisation technique of using tabu search to find neigbourhood solution which helps us swap nodes across routes such that it minimises operational cost for both routes.
For more info. on tabu search in context of transportation or vehicle routing problem please visit [Tabu Search](https://smartmobilityalgorithms.github.io/book/content/TrajectoryAlgorithms/TabuSearch.html#:~:text=Tabu%20search%20(TS)%20is%20an,local%20optima%20can%20be%20escaped.)

7. We create two utility functions for tabu search and neighbourhood generation.
{% gist e51bc7cc576026dc120e80a57a53e0ec neigbourhood_generation_func.py %}
{% gist e51bc7cc576026dc120e80a57a53e0ec tabu_search.py %}

8. Post this all the possible routes that were generated earlier are passed to the tabu search to do inter node swapping and yielding the best possible solutions in terms of cost of route.
{% gist e51bc7cc576026dc120e80a57a53e0ec candidate_solutions.py %}

9. Now these candidate solutions needs to be filtered out with some other constraints like time window.
{% gist e51bc7cc576026dc120e80a57a53e0ec remove_invalid_routes.py %}

10. Finally leaving us with calculation of most feasible route with minimum cost amongst all the candidate solutions.
{% gist e51bc7cc576026dc120e80a57a53e0ec final_solution.py %}

Hope you found this whole blog interesting, although definitely not the best solution ours was something to consider and thus got us ***Silver prize*** :man_dancing: :man_dancing: for {% include elements/highlight.html text="6th position among 23 IIT teams" %} that participated.
