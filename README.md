# DockerJIG
A **Docker** solution to **J**Meter + **I**nfluxDB + **G**rafana performance testing suite.

Have you recently built a web app and wish to conduct some performance testing on it? DockerJIG could be your solution!

## How it works in a nutshell
JMeter runs the load test, the results of the test are stored in InfluxDB, and Grafana reads the results from InfluxDB and visualizes them into graphs and dashboards. Docker eliminates all manual setup steps and packages everything together.

## How to use it
- Clone the repo by running `git clone https://github.com/jlight99/docker-jig.git`
- Navigate to the test folder of the repo by running `cd docker-jig/jmeter/test`
- Edit the user.properties file, change the webUrl property's value to the URL of your web app or whatever web server you want to put load on
- Run `docker-compose up` to start the load test and `docker-compose down` to stop the test
- Open localhost:3000 to see the Grafana web interface. Click into the default dashboard or create your own!

## How to configure it
To run your own JMeter test plan:
- copy the test plan into docker-jig/jmeter/test
- edit docker-compose.yml and replace the value of the JMETER_TEST environment variable with the file name of your test plan
- run `docker-compose up` again to execute your test plan

## Want to learn more about it?
Want to learn more about how this solution actually works and how I implemented it? Feel free to read the [medium article](https://medium.com/@ellenhuang523/a-docker-solution-to-jmeter-influxdb-grafana-performance-testing-568848de7a0f)!

