---
description: >-
  this document will try to explain about what is SOLID and give example how to
  implement it
---

# SOLID Principles

## S - Single Responsible Principles (SRP)

Details:

need to try have 1 actor handle 1 type of actions. means if we do some changes / adding new features only certain part got involved

Example:

* Repositories&#x20;
  * Contracts for data access
  * Technology agnostic
* Services
  * Business workflows
  * Application rules
  * Orchestrate repositories
* Adapters
  * Implement repository interfaces
  * Prisma / HTTP / Redis / S3
* Controller
  * Input validation
  * Call services
  * Error mapping
* Route&#x20;
  * HTTP wiring
  * Middleware
  * Request/response binding
* Domain
  * Entities
  * Value Objects
  * Domain rules

## O - Open Closed Principles

Details:

We need to have Closed for modification, but open for extend and add new features

Examples:

Let say current situation Adapter is using Prisma without Cache. then we want to implement the cache with Redis. means we no need to touch "Router", "Repository" and "Services" we only need to create new "Adapters" which is using Cache

Implementations:

1. Repository

```typescript
// repositories/UserRepository.ts
export interface UserRepository {
  findById(id: string): Promise<User>
}

```

2. Services

```typescript
// services/GetUserService.ts
import { UserRepository } from '@/repositories/UserRepository'

export class GetUserService {
  constructor(private readonly userRepo: UserRepository) {}

  async execute(id: string) {
    return this.userRepo.findById(id)
  }
}

```

3. Adapter Prisma

```typescript
// adapters/PrismaUserRepository.ts
import { UserRepository } from '@/repositories/UserRepository'
import { prisma } from '@/infra/prisma'

export class PrismaUserRepository implements UserRepository {
  async findById(id: string) {
    return prisma.user.findUnique({ where: { id } })
  }
}
```

4. Controller

```typescript
// controllers/UserController.ts
import { GetUserService } from '@/services/GetUserService'

export class UserController {
  constructor(private readonly getUser: GetUserService) {}

  async getById(req, res) {
    const user = await this.getUser.execute(req.params.id)
    res.json(user)
  }
}

```

5. How to use it

```typescript
const userRepo = new PrismaUserRepository()
const getUserService = new GetUserService(userRepo)
const controller = new UserController(getUserService)

```

6. Let's add new adapter using cache

```typescript
// adapters/CachedUserRepository.ts
import { UserRepository } from '@/repositories/UserRepository'

export class CachedUserRepository implements UserRepository {
  constructor(
    private readonly baseRepo: UserRepository,
    private readonly redis: RedisClient
  ) {}

  async findById(id: string) {
    const cached = await this.redis.get(`user:${id}`)
    if (cached) {
      return JSON.parse(cached)
    }

    const user = await this.baseRepo.findById(id)
    await this.redis.set(`user:${id}`, JSON.stringify(user))
    return user
  }
}

```

7. then just update the "how to use"

```typescript
const prismaRepo = new PrismaUserRepository()
const cachedRepo = new CachedUserRepository(prismaRepo, redis)

const getUserService = new GetUserService(cachedRepo)
const controller = new UserController(getUserService)

```

by this we not doing any modification on `prismaRepo` we only do extended for `cachedRepo` that's very maintainable

## L - Liskov Subtitutes Principles (LSP)

Details:

Make sure it will be really easy to switch. and make sure it will be always using the same contract same return as well

Example:

Let say now on the top example we want to change `prismaRepo` to `httpRepo` . Let's say this application no longer take the data from prismaRepo.

Implementations:

1. Create httpRepo / adapter

```typescript
// adapters/PrismaUserRepository.ts
import { UserRepository } from '@/repositories/UserRepository'
import { http } from '@/infra/http'

export class HttpUserRepository implements UserRepository {
  async findById(id: string) {
    const result = await http.get("http://someurl.com/api/v1/users");
    return result;
  }
}
```

2. Update how to use

```typescript
const httpRepo = new HttpUserRepository()
const cachedRepo = new CachedUserRepository(httpRepo, redis)

const getUserService = new GetUserService(cachedRepo)
const controller = new UserController(getUserService)

```

by this we really easy to switch between `PrismaRepo` to `HttpRepo`

## I - Interface Segregated Principles

Details:

Client should not forced to depend on interface they not use

Example:

let say we have interface like this

```typescript
export interface UserRepository {
  findById(id: string): Promise<User>
  findAll(): Promise<User[]>
  create(user: User): Promise<void>
  update(id: string, user: User): Promise<void>
  delete(id: string): Promise<void>
}
```

let say now only for `PrismaAdapter` we need `banned` it will be good to have another interface instead of include here, why?? because `HttpAdapter` doesn't need to implement it (let's say like that ya)

Implementations:

```typescript
export interface UserRepository {
  findById(id: string): Promise<User>
  findAll(): Promise<User[]>
  create(user: User): Promise<void>
  update(id: string, user: User): Promise<void>
  delete(id: string): Promise<void>
}

export interface UserBannedRepository {
  banned(id: string, user: User): Promise<void>
}
```

then on `PrismaAdapter` we can just update it like

```typescript
// adapters/PrismaUserRepository.ts
import { UserRepository } from '@/repositories/UserRepository'
import { prisma } from '@/infra/prisma'

export class PrismaUserRepository implements UserRepository, UserBannedRepository {
  async findById(id: string) {
    return prisma.user.findUnique({ where: { id } })
  }
  
  async banned(id: string, user: User) {
   return prisma.user.edit({data: user, where: {id}})
  }
}
```

## D - Dependency Inversion Principles

Details:

High-level modules should **not depend on low-level modules**.\
Both should depend on **abstractions**.

Example:

have a look on `Adapters` (low level modules) also have a look on `Services` (high level modules) both are depends on abstraction not dependent each other

Implementations:

```typescript
export class PrismaUserRepository implements UserRepository {
  async findById(id: string) {
    return prisma.user.findUnique({ where: { id } })
  }
}

```

```typescript
export class HttpUserRepository implements UserRepository {
  async findById(id: string) {
    const result = await http.get('/users/' + id)
    return result
  }
}

```

```typescript
const userRepo = new PrismaUserRepository()
// or
const userRepo = new HttpUserRepository()

const service = new GetUserService(userRepo)

```

by this we looking at services is agnostic with adapter, we not relay only with 1 adapter on service layer
