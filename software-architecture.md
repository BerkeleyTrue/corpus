---
title: software-architecture
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
      ubiquitous, it can lead to accidental complexity
    * Business Growth: A domain increases in complexity more often the
      decreases.

# Cap Theorem

* Theory in the consensus
* No algorithm can provide more than two of the three
  * Consistancy
  * Availability
  * Partition Tolerance
* Consistancy:
  * Where every read to the data receives the most recent write
* Availability:
  * Where every request receives a response, but no guarantee that it is the
    most recent
* Partition Tolerance:
  * Where the network continues to function despite delay/lost/dropped messages
    on the network
* Modes of failure:
  * Fail-stop: Participant drops from the network (crash) and does not recover
  * Fail-recover: Participant drops form the network but returns at some time n.
    (processing delays, network delays)
  * Network Partition: A member is separated from the others due to network
    failure
    * imagine a network of 5 members. This failure would be where 2 of the three
      members enter into their own subnet separated from the others. They still
      work together and with clients but now there are two partitions of the
      same network.
  * Byzentine Failure: A member exhibits arbitrary, conflicting, or malicious behavior (traitor scenerio)

# RAFT Consensus

* Terms: Leader, Follower, Client, Log
  * Client sends data. isn't a participant
  * Leader sends data to followers
  * Followers receives data
  * Log: Stores the data
* All data flows from Client to Leader to Followers
* Term:
  * Logical clock
  * inceases monotomically
  * Starts with an election
    * Network cannot receive data from a client until after an election
  * Follows by a period of log propogatoin
* Leaders - Serve for entire term until they fail
* All members start as followers
* Any follower can become leader if they meet certain criteria
* Followers - Have random election timeout
* Follower times out and becomes candidate
  * Votes for itself
  * sends vote request to other followers
    * If the followers log is longer than the candidate or at a higher index
      they vote no
    * If the follower has voted in the current term, they vote no
    * If the follower has heard from the current leader of the term within their
      election timeout, they vote no
    * Otherwise they vote yes
* Followers start election if they don't receive a  heart beat or append of logs
  within the minimum election timeout
* Leader is the only member that can receive data
  * Proposes a log entry to the followers
  * Responds to client with commit message when the majority of followers have
    responded
  * Can never delete messages
  * If client has sent data in some timeframe t, the Leader will send a
    heartbeat message to followers
* messages:
  * are idempodent, can be sent multiple times but only have effect
    once
  * contain info about Leaders log
    * a new entry and the preceding log
* Followers
  * can accept message
  * if entry is from a heigher term, it updates it's own term
  * if log entries not match it can reject them
* Leaders respond to reject entries
  * leader sends logs entries to the follower inverse-chronologically until it finds one the
    matches the followers, then deletes all the incorrect ones and appends all
    the following leader messages
