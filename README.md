# Re-Target
An email targeting and scheduling api for effective B2C and B2B email targeting and sales optimization.


## Steps to Setup

**1. Clone the application**

```bash
git clone https://github.com/jai-k-gohil/Re-Target.git
```

**2. Create MySQL database**

```bash
create database <your_db>
```

**3. Change MySQL username and password as per your MySQL installation**

open `src/main/resources/application.properties`, and change `spring.datasource.username` and `spring.datasource.password` properties as per your mysql installation


**4. Setup Spring Mail**

The project is using gmail's SMTP server for sending emails. Using Gmail or any other SMTP server, you'll need to configure the following mail properties accordingly -

```properties
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=
spring.mail.password=
```

If you're using Gmail, you need to allow the third party apps to send emails by following the instructions below -

+ Click [here](https://myaccount.google.com/security?pli=1#connectedapps)
+ Set ‘Allow less secure apps’ to YES

**5. Create DB Tables**

The project stores all the scheduled Jobs in MySQL database. You'll need to create the tables that Quartz uses to store Jobs and other job-related data. Please create required tables by executing the `db.sql` script located inside `src/main/resources` directory.

```bash
mysql> source <PATH_TO_DB.sql>
```

**6. Build and run the app using maven**

Finally, You can run the app by typing the following command from the root directory of the project -

```bash
mvn spring-boot:run
```

## Scheduling emails using the /scheduleEmail API

```bash
curl -i -H "Content-Type: application/json" -X POST \
-d '{"email":"someone@example.com",
    "subject":"Things I wanna say to my Future self","body":"Dear Future me, <br><br> <b>Think Big And Don’t Listen To People Who Tell You It Can’t Be Done. Life’s Too Short To Think Small.</b> <br><br>",
    "dateTime":"2018-09-04T16:15:00",
    "timeZone":"Asia/Kolkata"}' \
http://localhost:8080/scheduleEmail
```