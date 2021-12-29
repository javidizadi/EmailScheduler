# EmailScheduler

### Video Demo : https://youtu.be/PgAgKIcnFA8

### Web Application Using Asp .Net Core Web API for Backend and ReactJs for Frontend
### It can schedule your emails for any time!

# How Does Work



## Backend

#### Quartz .Net is an Enterprice Timer Library for .Net Standard Framework. I used it in this project for Scheduling Emails with cron Expression. In Project used as Hosted Service. for Communications with this service i used Events, means i send an object with a method from "ScheduleManager" Object and QuartzHostedService Recived it from a Delegate.
#### I Used EF Core and Sqlite for Save Schedules Data in Server. "ScheduleLoader" HostedService when server is Restarted gets uncompleted Schedules from Database and Reschedules their.

## Frontend
#### I Used tailwindcss and daisyui for User Interface Components.
#### in Project Used Axios for Communications with Web API. "http-client" Handles Authentication, "AccountManager" Service Handles Login and Signup and Change Password. for Manage Schedules Created "ScheduleManager" Service for CRUD Schedules.


## Diagram
### Here is a simple Diagram of Schedules an Email
![GitHub Light](/docs/schedule_diagram_light.svg#gh-light-mode-only)
![GitHub Dark](/docs/schedule_diagram_dark.svg#gh-dark-mode-only)


# Links
### Backend Repo : [EmailScheduler-WebApi](https://github.com/javidizadi/EmailScheduler-WebApi)
### Frontend Repo : [EmailScheduler-Frontend](https://github.com/javidizadi/EmailScheduler-Frontend)
### [Quartz .Net](https://www.quartz-scheduler.net)
### [Cron Expression](https://docs.oracle.com/cd/E12058_01/doc/doc.1014/e12030/cron_expressions.htm)
### [Tailwind CSS](https://tailwindcss.com)
### daisyUI Repo : [daisyui](https://github.com/saadeghi/daisyui)


# How to Run Project

## Backend
First you should set this parameters for config project using run `dotnet user-secret set ["key"] "value"` in root of Project
```
dotnet user-secrets set ["SMTP:Host"] "<your mail server IP or URL>"
dotnet user-secrets set ["SMTP:Port"] "<your mail server Port>"
dotnet user-secrets set ["SMTP:Username"] "<your Username in mail server>"
dotnet user-secrets set ["SMTP:Password"] "<your Password in mail server>"
dotnet user-secrets set ["SMTP:From"] "<your Full Email Address in mail server>"

dotnet user-secrets set ["JWT:Secret"] "<Your JWT Secret Key>"

```
you should set cors-policy address that it is your website address ( Frontend ) 


now you can run web application using `dotnet run -c=Release` and Use it!

find this lines in Program.cs file : 
```
app.UseCors(p =>
{
    p.AllowAnyHeader();
    p.WithMethods("GET", "POST", "PUT", "DELETE");
    p.WithOrigins("your_website_URL");
});

```

## Frontend
first you should set backend address at /src/Services/http-client , find this line:
```
this.client = axios.create({baseURL: "your_backend_address"});
```
and you can build it with commands :
```
yarn
yarn build
```
and copy content of /dist folder at your static host wwwroot and Enjoy it!
