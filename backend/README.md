#  Cat Rescue Portal Backend API

Enterprise-grade backend API for cat rescue operations, designed for high traffic and scalability.

##  Quick Start

```bash
# Install dependencies
dotnet restore

# Run the API
dotnet run
```
## Project Structure

```plaintext
├── appsettings.Development.json  # Development environment settings
├── appsettings.json             # Production environment settings
├── Backend.http                 # API endpoint definitions
├── Backend.sln                  # Visual Studio solution file
├── src/                         # Source code directory
│   ├── CatRescueApi/           # Main project
│   │   ├── Controllers/        # API endpoints
│   │   │   ├── AdoptionsController.cs
│   │   │   ├── BreedsController.cs
│   │   │   ├── CatsController.cs
│   │   │   └── UserController.cs
│   │   ├── DTOs/              # Data transfer objects
│   │   │   ├── AddressDto.cs
│   │   │   ├── AdoptionDto.cs
│   │   │   ├── BreedDto.cs
│   │   │   ├── CatDto.cs
│   │   │   ├── LoginResponseDto.cs
│   │   │   └── UserDto.cs
│   │   ├── Models/            # Business domain models
│   │   │   ├── Adoption.cs
│   │   │   ├── Breed.cs
│   │   │   ├── Cat.cs
│   │   │   ├── Result.cs
│   │   │   └── User.cs
│   │   ├── Services/          # Business logic
│   │   │   ├── AdoptionService.cs
│   │   │   ├── BreedService.cs
│   │   │   ├── CatService.cs
│   │   │   ├── DataService.cs
│   │   │   └── UserService.cs
│   │   └── Validators/        # Input validation
│   │       ├── AdoptionValidator.cs
│   │       ├── BreedValidator.cs
│   │       ├── CatValidator.cs
│   │       └── UserValidator.cs
│   └── Data/                  # JSON storage files
│       ├── applications.json  # Adoption applications
│       ├── breeds.json        # Cat breeds
│       ├── cats.json          # Available cats
│       └── users.json         # User information
└── tests/                     # Unit and integration tests
    └── CatRescueApi.Tests/     # Test project
        ├── Controllers/       # Controller tests
        ├── DTOs/             # DTO tests
        ├── Models/           # Model tests
        └── Services/         # Service tests
```
##  Configuration
### ⚠️ Warning: Do Not Commit This File
### Steps to Create `appsettings.json`

1. Create a file named `appsettings.json` in the root directory of the project.
2. Add the following configuration:

```json
{
  "JwtSecretKey": "your-secret-key",
  "MailgunDomain": "your-mailgun-domain",
  "MailgunApiKey": "your-mailgun-api-key",
  "SenderEmail": "your-sender-email"
}
```
Add these settings to `appsettings.json`:
Ensure that `appsettings.json` is listed in `.gitignore` to avoid accidentally committing sensitive information.

##  Core Features

- Multi-tenant support for different rescue organizations
- JWT authentication and email verification
- Comprehensive input validation
- Tenant-based data isolation
- Health monitoring and API documentation

##  API Endpoints

### Authentication

```http
POST /api/users/register    # Create new user
POST /api/users/login     # Get JWT token
```

### Cats

```http
GET /api/cats           # List cats for tenant
GET /api/cats/{id}      # Get specific cat
POST /api/cats/register # Register new cat
```

### Breeds

```http
GET /api/breeds         # List all breeds
GET /api/breeds/{id}    # Get specific breed
GET /api/breeds/filter  # Filter breeds
```

### Adoptions

```http
POST /api/adoptions     # Submit adoption
GET /api/adoptions/{id} # Get adoption status
PUT /api/adoptions/{id}/status # Update status
```

##  Security

- Include JWT token in Authorization header:
```http
Authorization: Bearer your-token
```


- Features:
  - JWT authentication
  - Email verification
  - Input validation
  - Password hashing (BCrypt)



##  Data Storage

Files in `./Data` directory:

- `users.json`
- `cats.json`
- `breeds.json`
- `applications.json`

##  Features

### Authentication & Authorization

- JWT token-based authentication
- Email verification system
- Role-based access control
- Tenant isolation

### Cat Management

- Comprehensive cat profiles
- Breed information integration
- Location-based services
- Status tracking

### Adoption System

- Multi-step adoption process
- Background check integration
- Status transitions
- Tenant-specific adoption tracking

### Data Management

- JSON-based storage
- TheCatAPI integration
- Tenant-specific data isolation
- Validation framework

##  Performance Considerations

- Optimized JSON storage access
- Efficient breed data caching
- Tenant-based data partitioning
- Asynchronous operations
- Request validation

##  Security Features

- JWT token validation
- Input sanitization
- Rate limiting
- Tenant isolation
- HTTPS enforcement

##  Dependencies

- ASP.NET Core 8.0
- FluentValidation
- BCrypt.Net-Next
- MailKit
- Swashbuckle.AspNetCore

##  Development

Run with `dotnet run`. Swagger UI available at `https://localhost:5197/swagger`.

## Sample Visualization - Authentication Flow

![alt text](AuthenticationFlowVisualization.png)

