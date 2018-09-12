# Part 16: Protecting our views with Guards

Protecting our views with Guards

So right now all of our views are accessible by anyone. If a non logged in user tries to access the route **/notes**, they will have access but they won’t see anything because they don’t have an access token.

What **Guards** will allow us to do is protect certain routes based on different criteria. So that we create rule of how users move throughout our application, whether logged in, or not.

Read more about Guards [here](https://angular.io/guide/router#milestone-5-route-guards).

## Step 1. Building out the our Auth Guard

We will start by creating a new folder called **guards** in our **app** folder. Then, following **Angular** naming styles, we are going to create a file called **auth.guard.ts**.

To restrict access based on who the user is we use the CanActivate class. With using this class we need to create a method called **canActivate\(\)**, that will run when this guard is called automatically.

The **canActivate\(\)** method needs to return a boolean observable, so let’s build that out.

![Logo Title Text 1](.gitbook/assets/00%20%288%29.PNG)

The method, checks to see if there is a access\_token currently in the localStorage then a user must be logged in. If there isn’t then we will navigate the user to the login screen. If there is a access\_token then they will be able to see the views that we restricted.

## Step 2. Implementing the Auth Guard on our paths

For us to use the auth guard we need to implement the canActivate guard on the path we are trying to restrict.

Let’s go to our **app.module.ts** file. And add it to our **notes** path.

![Logo Title Text 1](.gitbook/assets/01%20%283%29.PNG)

Then we need to add the Auth Guard to our providers property located in the **@NgModules** Decorator.

## Step 3. Running through Slight design changes here and there

For a style change, I am fond of adding some padding for our main content. We are going to add a **div** with a container around out **router-outlet** directive in the **app.component.html** file. And then, add the **container** class in the **app.component.css**

![Logo Title Text 1](.gitbook/assets/02%20%286%29.PNG)

![Logo Title Text 1](.gitbook/assets/03%20%2810%29.PNG)

