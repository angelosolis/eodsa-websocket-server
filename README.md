# EODSA WebSocket Server

Real-time WebSocket server for EODSA backstage management system.

## Features

- **Real-time Performance Reordering**: Drag & drop with instant sync
- **Multi-role Support**: Backstage, Announcer, Registration, Media, Judges
- **Status Management**: Ready, Hold, In Progress, Completed states
- **Presence Tracking**: Mark contestants as present/absent
- **Cross-platform CORS**: Supports multiple domains

## Environment Variables

Required for production deployment:

```env
PORT=3001
ALLOWED_ORIGINS=https://eodsa.vercel.app,https://www.avalondance.co.za
FRONTEND_URL=https://eodsa.vercel.app
NODE_ENV=production
```

## Deployment

This server is configured for deployment on:
- Render.com (recommended - free tier)
- Railway.app
- Heroku
- Any Node.js hosting platform

## Health Check

The server includes a health check endpoint at `/health` that returns:

```json
{
  "status": "healthy",
  "timestamp": "2024-01-01T12:00:00.000Z",
  "connectedClients": 5
}
```

## Usage

After deployment, update your main EODSA application with:

```env
NEXT_PUBLIC_SOCKET_URL=https://your-websocket-server-url
```

## Socket.io Events

### Client → Server
- `join:event` - Join event room
- `join:backstage` - Join backstage role
- `join:announcer` - Join announcer role
- `join:registration` - Join registration role
- `join:media` - Join media role
- `performance:reorder` - Reorder performances
- `performance:status` - Update performance status
- `presence:update` - Update contestant presence

### Server → Client
- `performance:reorder` - Broadcast reorder changes
- `performance:status` - Broadcast status changes
- `presence:update` - Broadcast presence changes
- `performance:announced` - Broadcast announcements
- `notification` - System notifications
