# Order Service - 12-Factor App Compliance

## Factor I: Codebase ✅
- **Single Repository**: This service has its own Git repository
- **Multiple Deploys**: Same codebase deploys to development, staging, and production
- **Independent Deployment**: Can be deployed separately from other services

## Factor II: Dependencies ✅
- **Explicit Declaration**: All dependencies declared in `package.json`
- **Isolation**: Uses npm for dependency management
- **No System Dependencies**: No reliance on system-wide packages

## Factor III: Config ✅
- **Environment Variables**: Configuration via environment variables
- **No Hardcoded Values**: Ports, URLs, and secrets configurable
- **Environment-Specific**: Different configs for dev/prod

## Factor IV: Backing Services ✅
- **RabbitMQ**: Treated as attached resource
- **Database Ready**: Can connect to external databases
- **Service Discovery**: Uses environment variables for service URLs

## Factor V: Build, Release, Run ✅
- **Build Stage**: `npm install` installs dependencies
- **Release Stage**: Code + config = release
- **Run Stage**: `npm start` runs the service

## Factor VI: Processes ✅
- **Stateless**: No local file storage or memory
- **Share-Nothing**: Each process is independent
- **Horizontal Scaling**: Multiple instances can run

## Factor VII: Port Binding ✅
- **Self-Contained**: Service binds to port 3000
- **No Web Server Dependency**: Express.js handles HTTP directly
- **Port Configuration**: PORT environment variable

## Factor VIII: Concurrency ✅
- **Process Model**: Can run multiple worker processes
- **Horizontal Scaling**: Multiple instances supported
- **Load Balancing Ready**: Stateless design supports load balancing

## Factor IX: Disposability ✅
- **Fast Startup**: Quick to start and stop
- **Graceful Shutdown**: Handles SIGTERM signals
- **Crash Recovery**: Can restart without data loss

## Factor X: Dev/Prod Parity ✅
- **Same Codebase**: Identical code in all environments
- **Same Dependencies**: npm packages in all environments
- **Same Backing Services**: RabbitMQ in all environments

## Factor XI: Logs ✅
- **Event Stream**: Logs written to stdout
- **No Log Management**: Service doesn't handle log files
- **Centralized Logging**: Logs captured by execution environment

## Factor XII: Admin Processes ✅
- **One-Off Tasks**: Database migrations, cleanup tasks
- **Same Environment**: Admin processes run in same environment
- **Same Codebase**: Uses same code as regular processes

## Deployment Commands

```bash
# Development
npm run deploy:local

# Production/VM
npm run deploy:vm

# Custom environment
NODE_ENV=production PORT=3000 npm start
```
