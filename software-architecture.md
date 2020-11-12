---
title: software architecture
---

# Strangler Pattern

* incrementally migrate software pattern
* Based on Strangler Fig Plant
  * Seeds germate in foreign tree branches.
  * Roots grow down the bark and take hold at the foot of the tree
  * Leafs/branches grow up past the tree canapy to grab/steal sunshine
  * Leaves/Branches/Roots will eventually snuff out the tree
  * Tree dies and rots away, leaving just the Strangler Tree (at this point
    called a columner tree as it is hollow)
* start with the biggest business win and least amount of effert
* implement a microservice (separate services by API (http))
* create anit-corruption layer
  * Interface between microservices and monolith
  * API to connect to service
  * Facade to interact with monolith
  * adapter to connect api to facade
  * Where this lives:
    * Can be whole in either the monolith or the service
      * Can and or do you want to modify the monolith
    * You can also do it in parts, where the facade lives in the monolith and
      the rest in the service or the api lives in the service and the rest lives
      in the monolith

# Command Query Responsibility Segragation (CQRS)

* Separate comands (writes) from Queries (reads)
* Separtion can even go to DB level
* Command DB's are pristine
* Query can target dbs which are highly de-normalized for UI/end user/analytics interfaces
* updates to UI are reactive (WS/SSE)
* Scaling can be done at service level
  * This means we can scale read/write services independently


# Event Sourcing

* Data is stored in a table of events vs tables per entity
* Event store changes to entities, not final state
* To get current state of an entity, fold over events
* To save time/compute snapshots of events can be made and stored in separate
  query databases for consumtion

# Domain Driven Design

* Core Domain: Ubiquitious Lanugage
  * Each term should have exactly one meaning
  * Since words on their own can have multiple meanings, we have to find a
    Bounded Context for these terms
* |- Support Sub-Domain: Bounded Context
  * A pattern that defines a strict boundry in which a term can be freely
    applied
* |- Generic Sub-Domain: Domain Implementation
  * How business implementation is done
  * Patterns:
    * Transaction Script
    * Active Record
    * Domain Model
    * Event Sourced Domain Model
  * More patterns can be found in "Patterns of Enterprise Software"
  * Can be dissoc from DDD, simplifing it
* Implications
  * Reduced complexity
    * Removing Tactical Modeling Patterns
    * without patterns, DDD becomes a system modeling methodology
  * Wider Applicativity
    * Communition: No matter how small the domain, if language is not
      ubiquitious, it can lead to accidental complexity
    * Business Growth: A domain increases in complexity more often the
      descreases.
