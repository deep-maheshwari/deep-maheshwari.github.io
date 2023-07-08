---
name: Kisaan Seva - D2C Web Portal for Farmers
tools: [React Js, Typescript, Node js, MongoDB]
image: ../static/Kissan-Seva-UI.png
description: This is a web portal project developed for farmers to sell their crops season to season via portal avoiding middle men monopoly.
---

<h3 style="text-align: center;">Kisaan Seva - D2C Web Portal for Farmers</h3>

There was a long running farmer's protest in India from `9 Aug 2020 – 11 Dec 2021` which was mainly due to the farm laws introduced by Indian government to avoid monoly of middle men coming in these markets. I was taking a Software Engineering course that time for which we(a team of four) had to choose a business idea for developing web project and learning software developemnt cycle form planning, development, testing to proper delivery. 

What could be a better oppportunity to take this project up for developing a web portal in times of such technological boom(in rural ares too) which allows farmers to stage mass produce of their crops and allow bidders to take them at a price sustainable for both. We also kept an informative content through our blogging features which could help flow of important market infromation, weather predictions, manuring crops in better way etc. 

This was a big project and {% include elements/highlight.html text="my contributions were primarily developing backend service using Node Js, MongoDB." %} and also I worked in {% include elements/highlight.html text="making recommendation system using Flask and ML libraries in Python" %} that would help recommend relevant blogs to farmers for their needs.

### Reason for choosing the tech stack we chose

- The frontend tech stack is React Js which is pretty standard and followed industry wide for reusable components. We added Next Js framework to the top of it to have better control over file structure and navigating through different pages in web portal. Used Typescript instead of Javscript for type safe implementation.

- The backend tech stack was chosen Node js due to it's simplicity for creating a server with CRUD operations basically following MVC design pattern. MongoDB was chosen because for our case there were minimal relations and preference was NoSQL database.

Do checkout our awesome website!

<p class="text-center">
{% include elements/button.html link="https://kisanseva.vercel.app/" text="Kisaan Seva" style="primary" %}
{% include elements/button.html link="https://github.com/deep-maheshwari/KisaanSeva" text="Frontend Repo" style="primary" %}
{% include elements/button.html link="https://github.com/deep-maheshwari/KisaanSeva-Backend" text="Backend Repo" style="primary" %}
</p>

