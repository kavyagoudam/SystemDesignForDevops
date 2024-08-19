# Micro Frontend Architectural Pattern

In Micro frontend architectural pattern, we split monolithic web application into multiple front end modules or libraries that act as independent single page applications. The splitting can be done by business capability or domain, just like we did in microservices. More importantly it is owned by a seperate team with full stack technical capabilities and the domain knowledge.

    All those micro-frontends are then assembled together at runtime by a container web application, when the user loads our site on their browser

Role of the container Application

1. Render common elements
2. Take care of common functionality
3. Tell each micro-frontend where/when to be rendered


Benefits of Micro-Frontends
1.  Replaced the complex monolithic codebase with small and manageable micro-frontends
2. Full-stack ownership of each micro-frontend
3.  Easier/Faster to test in isolation
4.  Seperate CI/CD pipeline
5. Seperate releases


Best Practices
1.  Micro-frontends are loaded at runtime
2.  No shared state in the browser
3.  Intercommunication through
    -   Custom event
    -   callbacks
    -   addressbar

