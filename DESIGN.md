# OAuth.XYZ Design Principles

This document outlines some of the guiding design principles of the Transactional Authorization (OAuth.XYZ) project.

## Minimize the front channel

The front channel is used only where user interaction is required. 

## HTTP-centric

Don't try to make things completely abstracted like WS*. 

Use HTTP features (headers, payloads) instead of just a carrier mechanism.

## Crypto agility

Signatures and encrpytion should be able to be layered.

Hashes used for handle confirmation should be selectable by the client/server. 


## Transactions

OAuth is a transactional protocol with multiple steps, whether it admits it or not. OAuth.XYZ always uses a transactional approach.

Transactions are started by a client calling the AS.
  - possibly by the client calling the RS, and the RS calling the AS


## Components

AS - authorization server
 - defined by a single entry endpoint (transaction endpoint)
 - other endpoints may also exist
   - interaction

## Common components

Whereever possible, use the same data structures and components for related elements. 

## Handles

"Handles" are effectively secrets that tie one call to the next one. They're handed by one party to another to be used in future parts of the transaction. 

Transaction Handle
 - created by AS
 - sent directly to client by AS in response


Client handle
 - created by AS or by registration (out of band)
 - proved by client
 

## Proving handles

Bearer
 - present handle value

Hash
 - Present hash of handle value
 - SHA3, SHA256, etc.
 
## Authentication

Client authenticates to server using handle and combination of secret keys. These must be tied to the transaction.
 - if client creates/holds secret, client authenticates the first time to prove access to its secret
 - if server generates the secret, client authenticates subsequent times

JWT

MTLS