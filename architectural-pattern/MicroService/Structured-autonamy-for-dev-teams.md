# Structured Autonomy for development Teams

## Full Team Autonomy Problems
 1. Upfront cost of infrastructure
 2. Infrastructure maintenance cost
 3. steep Learning curve
 4. Non-unifrom API
 

even though the whole point of microservice architecture is to be idependent teams, but the key to successfull microservices architecture is the balance between team autonomy and Structure.


 ## Structured autonomy

 Structured autonomy means each team is autonomous , but only within certain boundaries which can be grouped into 3 tiers.

Autonomy can be grouped into 3 tiers.
1.  Fully restrictive
    certain areas of the microservice should not be under each team, which should be same accross the entire porject.
    example:
        Infrastructure:-
            1.  Monitoring and alerting
            2. CI/CD
        API guidelines and best practices
        security and data compliance

2.  Freedom with Boundaries
    Allowing some teams some freedom, but within some boundaries.
    example
        Programming Languages
        Database technologies

3. Complete Autonomy
    Each team can work entirely independently from other teams.
    Example:
        Release process
        Release schedule and frequency
        Custom scripts for local development and testing
        Documentation

Factors that can influnce the boundaries of teams autonomy
    - Devops/SRE team influence
    - Developers seniority
    - Company;s culture