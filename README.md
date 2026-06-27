# AI UI Tutor

Monorepo scaffold for an app that accepts a UI screenshot, asks OpenAI to identify the interaction steps, and returns the original image with numbered guidance drawn on top.

## Structure

```text
.
|-- ai_services/          # OpenAI vision prompt and response parsing
|-- backend/              # FastAPI API and image annotation renderer
|-- frontend/             # Next.js user interface
|-- docker-compose.yml
`-- .env.example
```

## Run with Docker

```bash
cp .env.example .env
# edit OPENAI_API_KEY in .env
docker compose up --build
```

Frontend: http://localhost:3000

Backend health check: http://localhost:8000/health

## API

`POST /api/analyze`

Form fields:

- `file`: image file
- `user_goal`: optional instruction describing what the user wants to do

Response includes detected steps and `annotated_image_data_url`, a PNG data URL that the frontend can render directly.
