# Kukkilan Biljardi - Copilot Instructions

## Architecture Overview

This is a full-stack billiard hall booking system with:

- **Backend**: Rust with Axum framework, MySQL database, SQLx for migrations
- **Frontend**: Next.js 15 with TypeScript, Tailwind CSS, App Router
- **Development**: Backend runs on port varies (see `config.rs`), frontend on :3000

## Key Patterns

### Backend Feature Structure

Each domain follows clean architecture in `src/features/{feature}/`:

```
mod.rs              # Exports routes function
routes.rs           # Axum route handlers, path extraction, JSON responses
service.rs          # Business logic layer
repository.rs       # Database access layer with SQLx
model.rs           # Database row structs
data_transfer_objects.rs  # API request/response types
```

### State Management

- `AppState` contains shared config and repositories
- Injected via `State(state): State<AppState>` in route handlers
- Access repositories like `state.bookings.create(body).await?`

### API Response Patterns

Use custom response types from `response.rs`:

- `Created<T>` for POST with location header
- `NoContent` for DELETE operations
- `Json<T>` for standard GET responses
- All routes return `Result<ResponseType, AppError>`

### Database Layer

- Migrations in `migrations/` with timestamp prefixes
- SQLx compile-time checked queries
- Foreign key constraints (calendars ↔ media, bookings ↔ calendars)
- UTC datetime storage with `DATETIME(6)` precision

## Development Workflows

### Backend Development

```bash
cd backend
cargo run  # Starts server, runs migrations automatically
docker-compose up -d  # Start MySQL container
```

### Frontend Development

```bash
cd frontend
npm install
npm run dev --turbopack  # Development with Turbopack
```

### Key Environment Setup

- Backend uses `.env` file for `DATABASE_URL`, `MEDIA_ROOT`, `MEDIA_BASE_URL`
- Frontend API calls use proxy pattern (see TODO in frontend/README.md)
- CORS configured for localhost:3000 in `main.rs`

## Frontend Conventions

### App Router Structure

- `(public)/` - Public pages (homepage, booking)
- `(admin)/` - Admin pages (protected routes)
- `api/` - API route handlers that proxy to Rust backend
- Route groups use parentheses for organization without affecting URLs

### API Integration

- `lib/api.ts` - Centralized API client with `apiFetch()` helper
- Server-side data fetching in page components with `await`
- Custom `getBaseUrl()` for SSR/client environment handling
- No caching by default (`cache: "no-store"`)

### UI Patterns

- `SectionWrapper` component for consistent section layout
- Responsive text classes (`text-responsive`, `space-y-responsive`)
- Tailwind for styling with custom CSS utilities in `globals.css`

## Database Schema Insights

Core entities:

- `calendars` - Booking calendars (snooker/pool tables)
- `bookings` - Customer reservations with contact info
- `media` - File uploads with content type validation
- Static content tables for notices, opening hours, contact info

## Security & Validation

- Admin routes need protection (see backend TODO)
- Customer data encryption planned
- File upload validation via `mime_guess` and `infer` crates
- Input validation layer planned but not implemented

## Testing Strategy

Testing framework not yet implemented - prioritize adding tests for:

- Repository layer with test database
- Service layer business logic
- API endpoint integration tests
