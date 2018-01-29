# Communicating with Web API with Auth Service

In this next section, we will be talking with a DotNet **WebAPI**! Now there is a few steps that you need to do to configure your **WebAPI**. But rather than setting up the **WebAPI**, we will stick with the Angular side and just use a pre-existing one. 

Here is the link we will be using for our WebAPI endpoints: 

http://kcpelevennoteapie.azurewebsites.net/Help 

What is a service? Great question, read mere in the link [here](https://angular.io/guide/architecture#services). We will continue assuming you know what the purpose of a **Service** is. 

I will tell you the reason why it’s important. It is our layer that will communicate to our WebAPI specifically; not our components, not our modules, not any other thing, only our services.

Strap in, [let’s do this](https://static1.squarespace.com/static/55f32473e4b029b54a7228d2/582b8a8fc534a5c177d16c67/582b8a9f2994cab6e0cdd61c/1479256368634/giphy-39.gif).

## Step 1. Using Angular CLI to build our Service

**Angular’s CLI** is very helpful in creating our components for us. 

But what else can it do? Well i’m glad you asked. The **CLI** can also generate our services for us! 

In your Terminal. 

Type: 
```shell
ng g s services/auth --no-spec (Remember g stands for generate, and the s stands for service)
```
![alt text](./images/0.006/00.PNG "Logo Title Text 1")

What was created was two things: 

- A folder called **services** which is where all of our services will be.
- A file called **auth.service.ts** inside of that folder.

But you might have a **WARNING**, we will pick this up in the next step.


## Step 2. Continuing where the CLI left off…

The compiler was very generous in creating the **services folder** and our **auth.service.ts** file for us but we need to continue with the setup from here. 
![alt text](./images/0.006/01.PNG "Logo Title Text 1")

In order to add our service to our application, we need to go the **app.module.ts** file and include our **auth.service** in the **providers** array within our **@NgModule** decoration. 

Why?...

Well, since in an Angular project can have multiple modules, Angular will not assume that you want to put your newly created service in the **app.module.ts** file.

![alt text](./images/0.006/02.PNG "Logo Title Text 1")

So we need to do that manually. 

## Step 3. Building Register Method then Making request using the built in HTTP Module

Now that we have are fresh and clean service, let’s add a [nice little](https://media.giphy.com/media/rYEAkYihZsyWs/giphy.gif) register method. 

What this method will do is take in an object that has 3 properties: 

- Email
- Password
- confimPassword 

Those  are the properties that we ask for when a user is registered. Also the properties that our **WebAPI** is [expecting](http://kcpelevennoteapie.azurewebsites.net/Help/Api/POST-api-Account-Register) to be inside of the request to be sent to the database.

Then our register method will need to send our data using an HTTP request to our API. 

Let’s start coding this. 

We need to hold the never changing value of our API link we will do that above the **@Injectable** decorator.

Type, 
```js 
const Api_Url = ‘http://kcpelevennoteapie.azurewebsites.net’;
```
![alt text](./images/0.006/04.PNG "Logo Title Text 1")


Then, under our **constructor** we will begin to add our register method.

## Step 4. building out RegisterUser Model 

As we are working with TypeScript, there are good practices to make methods such as our Register method “type safe.”

One of those ways in creating a Model that the data we are looking to receive has the correct properties, and if it doesn’t, we should see a big fat red squiggly line.

Create a folder within the **app folder** called **models**.

![alt text](./images/0.006/05.PNG "Logo Title Text 1")


Inside of that file we are going to create a file called **RegisterUser.ts**. Place this code inside.
Back in our **auth.service** we can now make sure the parameter that we are accepting will have everything that is inside of our **RegisterUser** Model by applying the type to the parameter.

![alt text](./images/0.006/06.PNG "Logo Title Text 1")


## Step 5. Import HttpClientModule to our Application

Angular comes pre-built with it’s own HTTP method, Read more [here](https://angular.io/guide/http#httpclient).

We are going to include it within our application so that we can use it to communicate with our WebAPI. 

In our **app.module.ts file**, import **HttpClientModule**, on line 5. We are going to keep our Angular library imports together above. 

Then let’s include it in our **@NgModule** decorator, within the **imports** property. Right above the **ReactiveFormsModule**.

Now we will be able to use it elsewhere in our application. 

![alt text](./images/0.006/07.PNG "Logo Title Text 1")

## Step 6. Injecting HTTP into our Service

To be able to use all the properties and methods of **HttpClientModule**, we need to [“inject”](https://angular.io/guide/dependency-injection-pattern#the-dependency-injection-pattern) an instance of it inside of our **auth.service** constructor. Let’s navigate back to our **auth.service.ts** file.

We create an instance of HTTP by assigning it to a private variable— we could use the accessor method of public as well, but since this variable will not be accessed to any other component we will keep it private.

![alt text](./images/0.006/08.PNG "Logo Title Text 1")

Then we can refer to it inside of our register method by using our keyword **“this”**. 

Once we call the assignment operator after our instance variable we see the list of methods and properties we can chain next. 

Since we are sending information to the WebAPI, which HTTP verb will we use?

Post! 

 Now we can finish off with building our Post Request to our WebAPI. 

![alt text](./images/0.006/Capture.PNG "Logo Title Text 1")


Notice the **back-ticks around the url**. These aren’t quotes!.  They allow us to utilize **string interpolation**. So we can use our variable that we’ve created above in line without using the **+ operator**.

Our auth.service.ts file should look like this now. _**Note: the endpoint should be api/Account/Register**_:

![alt text](./images/0.006/10.PNG "Logo Title Text 1")

## Step 7. Using our Register Method in our Register Controller

Now that we have the **register** method created in the **auth.service.ts**, let’s put it to work!

In our registration controller (**registration.component.ts**), we have an **onSubmit()** method that is just returning a **console.log**.

This is where we are going to use our **register** method. Now for us to have access to that method, we first need to “inject” an instance of the Auth Service. 

Inside of the constructor is where that happens. 

![alt text](./images/0.006/11.PNG "Logo Title Text 1")

Since we have an instance, we can include it into our method **onSubmit()**.

![alt text](./images/0.006/12.PNG "Logo Title Text 1")

Volia!
