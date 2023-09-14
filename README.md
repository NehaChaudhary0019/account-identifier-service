# account-identifier-service

Account Identifier Service
The Bank Account Service will use the Feign/Ribbon client to load balance calls to the Account Identifier Service. The Account Identifier Service exposes a single REST endpoint that takes an AccountType parameter and returns an AccountIdentifier . The AccountIdentifier contains a randomly generated account number and the port of the instance that handled the request. Including the port in the response will allow us to see which instance handled the request and will prove that Ribbon is load balancing the requests as expected.

To see the load balancing in action, we're going to run 2 instances of the Account Identifier Service. One app will run on port 8091 and the other on port 8090. It's important you use these specific ports as these are the ports we used to configure Ribbon earlier. Start the first instance by running java -jar target/account-identifier-service-1.0.0.jar --server.port=8091
and the second instance by running java -jar target/account-identifier-service-1.0.0.jar --server.port=8090.

