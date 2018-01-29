# Setup with the Angular CLI 

### Step 1. Set up the Development Environment

JavaScript is a web focused language, in order to use any type of JavaScript off the web we need to first install Node. Node is the runtime that allows our computers to understand JS offline. 

You might already have Node installed. You can check by going to your command line in any directory and running **node -v**. If you have it, it will tell you the version of Node you are running. If you don’t have it, install Node.js and npm.

With installing Node comes NPM (Node Package Manager). NPM allows developers to install JS based applications, code snippets, libraries, etc. to our machines.  It’s a lot like Nuget package manager.
### Step 2. Install Angular CLI

After Node installer is finished go ahead and open your command line. Let’s install angular CLI. The directory will not matter, since the **-g** flag stands for ‘global’.

In any directory type:
```shell 
npm install -g @angular/cli
```
![alt text](./images/0.000/01.PNG "Logo Title Text 1")

Again, the **-g** command installs a resource to your global **node_modules** folder. 

Patience is a virtue, installation with resources could take time!

Navigate to where you would like to install this application through your terminal. 
### Step 3. Create Angular Skeleton

We can now generate a new skeleton application with the Angular CLI. We will want to CD into the root of our project and run the following command:
```shell
ng new ElevenNote.WebAngular
```
![alt text](./images/0.000/02.PNG "Logo Title Text 1")

**(Note: that the image below has a little different naming convention)**.

Again, patience is needed for our app to be scaffolded out. 

Once it’s finished, change your directory into your newly created folder **ElevenNote.WebAngular**.

Type: 
```shell 
cd ElevenNote.WebAngular
```

To run the application so that we can see the output in our browsers we use the command:
```shell
 ng serve --open
```
You should see the scaffolded Angular starter code, as seen in the following image:

![alt text](./images/0.000/03.PNG "Logo Title Text 1")

This is the pre-generated code that comes with the Angular skeleton. Let’s head to our code editor.

In your terminal, since we are using Visual Studio Code as our IDE we can use the command, **code**

Type: 
```shell
code . ( ← don’t forget the period)
```
![alt text](./images/0.000/04.PNG "Logo Title Text 1")


TODO An overview of the folders and files

### Step 4. Familiarizing Ourselves with the Project

Inside of VS Code, open the **src —> app** folder, 

There are a lot of files, we will cover a quick example of what all of these do in Angular Folder and File Guide.

We will be working mostly in the **app** folder. 

There will be times when we will be in the src folder changing the **style.css** and the **index.html** files.

The **app** folder is where all of our components will live and be created. 

There are 4 files that have the .component name convention appended to them:

- CSS file 
- HTML file 
- Spec.ts file 
- Ts file 

![alt text](./images/0.000/05.PNG "Logo Title Text 1")

These 4 files together are a build out  of the boilerplate component that comes right out of the box from the **ng new <app name>** command.

You’ll notice that these 4 files are like a full eco-system of a component. The **CSS** file to pull out our styles. The **HTML** for the skeleton of a web view. The **TypeScript** (spec.ts) test file. Then the **TypeScript** file that houses all of our functionality.

### Step 5. Remove Some Boilerplate information

Let’s navigate to the **index.html** file

![alt text](./images/0.000/06.PNG "Logo Title Text 1")

Remove all the code inside of that file, since it’s just boilerplate, we will put in our own information there. 

In the **app.component.ts** file we can also remove the line of code that has the member property called **title**.
### Step 6. Taking a look at the final file

Let’s open up the sixth file that is in the **app** directory, **app.module.ts**

![alt text](./images/0.000/07.PNG "Logo Title Text 1")


The **app.module.ts** file is where all of our components, services, modules, guards, custom directives, etc. All of these different things that will make up our application will be added to. In order for us to organize our application into a block of functionality. 

Notice the **@NgModule({...})**—this is a class decorator. This builds the root application with the components, services, guards, custom directives, and other modules that we build and what we can include from third party services. 

There were a few keywords in the last paragraph that are not explained just yet, but please be patient, we will get there! 

**@NgModule({...})** has an assortment of keys for the object, let’s define: 

- **Declarations**: Which components, directives, and pipes belong to the NgModule
- **Imports**: Other NgModules with components, directives, and pipes by the components in this NgModule
- **Providers**: Services at the application level that any application component can use.
- **Bootstrap**: the app with one or more top-level, root components

We have completed our application setup thus far, let’s add some code in the next section. 

