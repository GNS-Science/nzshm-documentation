# NSHM Domain Model

Diagrams depicting the Conceptual model of the NSHM project including  both behavior and data. See also [Wikipedia](https://en.wikipedia.org/wiki/Domain_model).

We use UML Class modelling techniques to explaing the Information used within the NZ NSHM ecosystem. Our diagrams use Mermaid, whcih makes them diagram-as-code

## Table of contents

 -  [Seismic Hazard Model](./seismic_hazard_model.md)


## CLASS DIAGRAM
 ```mermaid
classDiagram
  Person <|-- Student
  Person <|-- Professor
  Person : +String name
  Person : +String phoneNumber
  Person : +String emailAddress
  Person: +purchaseParkingPass()
  Address "1" <-- "0..1" Person:lives at

  class Student {
    +int studentNumber
    +int averageMark
    +isEligibleToEnrol()
    +getSeminarsTaken()
  }

  class Professor {
    +int salary
  }
  class Address {
    +String street
    +String city
    +String state
    +int postalCode
    +String country
    -validate()
    +outputAsLabel()  
  }
```