# Email Scheduler

### Demo video : https://youtu.be/PgAgKIcnFA8

### a Web Application written in Asp .Net Core Web API for back-end and ReactJs for front-end
### It can schedule your emails for any time!

# How does work
## Back-end

#### Quartz .Net is an enterprice timer library for .Net Standard Framework. I used it in this project for scheduling emails with cron expression.
#### I Used EF Core and Sqlite for storing schedules in server. "ScheduleLoader" Hosted Service gets uncompleted schedules from database and reschedules them when server booted up.

## Frontend
#### I used tailwindcss and daisyui for user interface components.
#### In this project i used Axios for communications with Web API. "http-client" handles authentication, "AccountManager" service handles login and signup and change password. "ScheduleManager" service created for manage schedules and CRUD actions for schedules.


## Diagram
### Here is a simple diagram of scheduling an email
![GitHub Light](/docs/schedule_diagram_light.svg#gh-light-mode-only)
![GitHub Dark](/docs/schedule_diagram_dark.svg#gh-dark-mode-only)


# Links
### Back-end Repo : [EmailScheduler-WebApi](https://github.com/javidizadi/EmailScheduler-WebApi)
### Front-end Repo : [EmailScheduler-Frontend](https://github.com/javidizadi/EmailScheduler-Frontend)
### [Quartz .Net](https://www.quartz-scheduler.net)
### [Cron Expression](https://docs.oracle.com/cd/E12058_01/doc/doc.1014/e12030/cron_expressions.htm)
### [Tailwind CSS](https://tailwindcss.com)
### daisyUI Repo : [daisyui](https://github.com/saadeghi/daisyui)


# How to Run Project

## Back-end
First you should set this parameters for config project using run `dotnet user-secret set ["key"] "value"` in root of project
```
dotnet user-secrets set ["SMTP:Host"] "<your mail server IP or URL>"
dotnet user-secrets set ["SMTP:Port"] "<your mail server Port>"
dotnet user-secrets set ["SMTP:Username"] "<your Username in mail server>"
dotnet user-secrets set ["SMTP:Password"] "<your Password in mail server>"
dotnet user-secrets set ["SMTP:From"] "<your Full Email Address in mail server>"

dotnet user-secrets set ["JWT:Secret"] "<Your JWT Secret Key>"

```
you should set cors-policy address that it is your website address ( Front-end ) 


now you can run web application using `dotnet run -c=Release` and enjoy it.

find this lines in Program.cs file : 
```
app.UseCors(p =>
{
    p.AllowAnyHeader();
    p.WithMethods("GET", "POST", "PUT", "DELETE");
    p.WithOrigins("your_website_URL");
});

```

## Fron-tend
first you should set backend address at /src/Services/http-client , find this line:
```
this.client = axios.create({baseURL: "your_backend_address"});
```
and you can build it with commands :
```
yarn
yarn build
```
and copy content of /dist folder at your static host wwwroot and enjoy it!
