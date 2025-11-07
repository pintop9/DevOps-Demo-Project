# GitHub Copilot Prompts for DevOps-Demo-Project

Curated prompts and chat modes for common tasks in this DevOps demonstration project.

## Table of Contents

- [Development Prompts](#development-prompts)
- [Testing Prompts](#testing-prompts)
- [Docker & Kubernetes Prompts](#docker--kubernetes-prompts)
- [CI/CD Prompts](#cicd-prompts)
- [Debugging Prompts](#debugging-prompts)
- [Documentation Prompts](#documentation-prompts)
- [Security Prompts](#security-prompts)
- [Performance Prompts](#performance-prompts)

---

## Development Prompts

### Adding New API Endpoints

```
Create a new Flask endpoint at /api/metrics that returns:
- Total requests count
- Average response time
- Current memory usage
- Uptime in seconds

Follow the existing pattern in app/main.py, include error handling, 
and write corresponding tests in tests/test_main.py.
```

### Implementing Middleware

```
Add Flask middleware to app/main.py that:
- Logs every request with method, path, and response time
- Adds correlation-id header to all responses
- Measures request duration
- Handles exceptions globally

Follow Python best practices and existing code style.
```

### Adding Configuration Management

```
Refactor app/main.py to use a configuration class that:
- Loads settings from environment variables
- Supports different environments (dev, staging, prod)
- Includes validation for required settings
- Uses dataclasses or pydantic for type safety
```

### Implementing Database Connection

```
Add SQLAlchemy database support to the Flask app with:
- Connection pooling configuration
- Migration support using Alembic
- Health check endpoint that validates DB connection
- Proper error handling and connection retry logic

Include necessary dependencies in pyproject.toml.
```

---

## Testing Prompts

### Writing Comprehensive Tests

```
Write comprehensive pytest tests for the Flask app in tests/test_main.py that cover:
- All existing endpoints (/, /health, /ready, /api/info, /api/echo)
- Success and error scenarios
- Edge cases and boundary conditions
- Mock external dependencies
- Achieve >85% code coverage

Use pytest fixtures appropriately.
```

### Integration Testing

```
Create integration tests for the Flask app that:
- Test the complete request-response cycle
- Validate JSON response schemas
- Test with real HTTP requests (not test client)
- Include performance assertions
- Test concurrent requests

Place in tests/integration/ directory.
```

### Load Testing Script

```
Create a Python script using locust or pytest-benchmark for load testing:
- Test all API endpoints
- Simulate 100 concurrent users
- Run for 5 minutes
- Generate performance report
- Include response time percentiles (p50, p95, p99)

Save as tests/load_test.py.
```

### Test Fixtures Library

```
Create a comprehensive pytest fixtures file tests/conftest.py with:
- Flask test client fixture
- Mock data fixtures for API responses
- Database fixtures (if applicable)
- Authentication fixtures
- Cleanup fixtures

Document each fixture with clear docstrings.
```

---

## Docker & Kubernetes Prompts

### Optimizing Dockerfile

```
Optimize docker/Dockerfile to:
- Reduce final image size to <100MB
- Implement multi-stage build effectively
- Use layer caching for faster builds
- Add security scanning in build process
- Include vulnerability scanning with trivy

Maintain existing functionality and Python 3.11.
```

### Creating Docker Compose for Development

```
Enhance docker/docker-compose.yml to include:
- Python Flask app with hot-reload
- PostgreSQL database with persistent volume
- Redis for caching
- Network configuration
- Environment variables from .env file
- Health checks for all services

Include comments explaining each section.
```

### Helm Chart Enhancements

```
Enhance helm/devops-demo/values.yaml and templates to support:
- Multiple environments (dev, staging, prod)
- External secrets management (ESO or sealed secrets)
- Service mesh integration (Istio)
- Network policies
- Pod security policies
- Resource quotas

Update templates accordingly and add values-dev.yaml, values-prod.yaml.
```

### Kubernetes Monitoring Setup

```
Create Kubernetes manifests in helm/devops-demo/templates/ for:
- ServiceMonitor for Prometheus scraping
- PodMonitor for detailed metrics
- Grafana dashboard ConfigMap
- Alert rules for critical conditions
- Logging sidecar configuration

Ensure compatibility with existing Helm chart structure.
```

---

## CI/CD Prompts

### GitHub Actions Workflow Enhancement

```
Enhance .github/workflows/ci.yml to include:
- Parallel testing across multiple Python versions (3.11, 3.12)
- Security scanning with Snyk or Trivy
- Code quality checks with SonarCloud
- Automated dependency updates
- Performance regression detection
- Slack notifications on failure

Maintain existing functionality.
```

### Deployment Pipeline

```
Create .github/workflows/deploy-staging.yml that:
- Triggers on merge to develop branch
- Deploys to staging Kubernetes cluster
- Runs smoke tests post-deployment
- Validates health endpoints
- Rolls back on failure
- Sends deployment notifications

Use existing CD workflow as reference.
```

### Release Automation

```
Enhance .github/workflows/release.yml to automatically:
- Generate changelog from conventional commits
- Bump version in all files (pyproject.toml, Chart.yaml)
- Create GitHub release with artifacts
- Build and push multi-arch Docker images
- Update Helm chart repository
- Trigger ArgoCD sync

Follow semantic versioning (semver).
```

### Automated Security Scanning

```
Create .github/workflows/security.yml that runs:
- SAST with Bandit for Python code
- Container image scanning with Trivy
- Dependency vulnerability check with Safety
- Secrets detection with TruffleHog
- License compliance checking

Schedule to run daily and on PRs.
```

---

## Debugging Prompts

### Troubleshooting Kubernetes Issues

```
I'm seeing CrashLoopBackOff for the devops-demo pod. Help me debug by:
1. Analyzing the pod logs pattern
2. Checking resource limits and requests
3. Validating liveness/readiness probe configuration
4. Examining ConfigMap and Secret references
5. Providing kubectl commands for investigation

Reference helm/devops-demo/templates/deployment.yaml.
```

### Analyzing Performance Issues

```
The Flask app response time is slow. Help me identify bottlenecks:
1. Add performance profiling to app/main.py
2. Identify slow endpoints
3. Suggest optimization strategies
4. Add performance monitoring
5. Implement caching where appropriate

Use Python profiling tools like cProfile or py-spy.
```

### Debugging CI/CD Failures

```
GitHub Actions workflow .github/workflows/ci.yml is failing. Help me:
1. Analyze the error logs
2. Identify root cause
3. Suggest fixes
4. Add better error handling
5. Improve debugging output

Focus on the test and build jobs.
```

### Memory Leak Investigation

```
The Flask app shows increasing memory usage over time. Help me:
1. Add memory profiling using memory_profiler
2. Identify potential memory leaks
3. Implement proper cleanup
4. Add monitoring for memory metrics
5. Set appropriate resource limits

Provide code examples and debugging commands.
```

---

## Documentation Prompts

### API Documentation

```
Update docs/API.md with:
- OpenAPI/Swagger specification for all endpoints
- Request/response examples for each endpoint
- Error codes and their meanings
- Rate limiting information
- Authentication requirements
- Code examples in Python, curl, and JavaScript

Generate from app/main.py endpoints.
```

### Architecture Diagram

```
Create a detailed architecture diagram in Mermaid format showing:
- Complete CI/CD pipeline flow
- GitHub Actions → Docker → Kubernetes → ArgoCD
- All components and their interactions
- Data flow between services
- Monitoring and observability stack

Save as docs/ARCHITECTURE.md.
```

### Troubleshooting Guide

```
Create docs/TROUBLESHOOTING.md with solutions for:
- Common deployment issues
- Pod startup problems
- Image pull errors
- ArgoCD sync failures
- Network connectivity issues
- Performance problems

Include kubectl commands and diagnostic steps for each issue.
```

### Contributing Guide

```
Enhance CONTRIBUTING.md with:
- Detailed setup instructions
- Code style guidelines with examples
- Git commit message conventions
- PR process and checklist
- Testing requirements
- Review process

Make it beginner-friendly with step-by-step instructions.
```

---

## Security Prompts

### Security Hardening

```
Enhance security of the Flask application:
1. Add input validation for all endpoints
2. Implement rate limiting
3. Add CORS configuration
4. Implement request size limits
5. Add security headers (CSP, HSTS, etc.)
6. Implement proper error handling (no info leaks)

Update app/main.py with security best practices.
```

### Kubernetes Security

```
Harden Kubernetes deployment in helm/devops-demo/:
1. Implement Pod Security Standards (restricted)
2. Add Network Policies for ingress/egress
3. Use SecurityContext with minimal privileges
4. Implement RBAC with least privilege
5. Add Pod Security Admission
6. Configure secret encryption at rest

Update templates and values.yaml accordingly.
```

### Secret Management

```
Implement proper secret management:
1. Integrate with External Secrets Operator (ESO)
2. Connect to AWS Secrets Manager or HashiCorp Vault
3. Update Helm charts to use external secrets
4. Remove hardcoded secrets
5. Add secret rotation mechanism

Provide configuration examples in helm/devops-demo/.
```

### Container Image Security

```
Enhance container security in docker/Dockerfile:
1. Use distroless or minimal base images
2. Scan for vulnerabilities with Trivy
3. Sign images with Cosign
4. Generate SBOM (Software Bill of Materials)
5. Implement image scanning in CI/CD
6. Add OCI image signing verification

Include GitHub Actions workflow updates.
```

---

## Performance Prompts

### Application Performance Optimization

```
Optimize Flask application performance in app/main.py:
1. Implement response caching for appropriate endpoints
2. Add connection pooling for external services
3. Optimize JSON serialization
4. Add request/response compression
5. Implement async request handling where beneficial
6. Add performance metrics collection

Benchmark before and after changes.
```

### Kubernetes Resource Optimization

```
Optimize Kubernetes resources in helm/devops-demo/values.yaml:
1. Right-size CPU and memory requests/limits based on actual usage
2. Configure HPA with appropriate metrics
3. Implement pod disruption budgets
4. Add pod topology spread constraints
5. Configure resource quotas
6. Optimize startup/liveness/readiness probes

Provide analysis and recommendations.
```

### Database Query Optimization

```
If database is added, optimize queries:
1. Add database indexing strategy
2. Implement query result caching
3. Use connection pooling effectively
4. Add query performance monitoring
5. Implement read replicas if needed
6. Add database query logging and analysis

Include SQLAlchemy best practices.
```

### Caching Strategy

```
Implement multi-level caching strategy:
1. Add Redis for application-level caching
2. Implement response caching for API endpoints
3. Add CDN configuration for static assets
4. Implement cache invalidation strategy
5. Add cache monitoring and metrics
6. Configure cache TTLs appropriately

Update docker-compose and Kubernetes manifests.
```

---

## Advanced Prompts

### Implementing Observability Stack

```
Implement complete observability stack:
1. Prometheus for metrics collection
2. Grafana for visualization with dashboards
3. Loki for log aggregation
4. Tempo for distributed tracing
5. OpenTelemetry instrumentation in Flask app
6. Alert manager for notifications

Create Helm chart in helm/observability/ and integrate with main app.
```

### Service Mesh Integration

```
Integrate Istio service mesh:
1. Add Istio sidecar injection annotations
2. Configure VirtualService and DestinationRule
3. Implement traffic splitting for canary deployments
4. Add circuit breakers and retry policies
5. Configure mTLS for service-to-service communication
6. Add telemetry collection

Update Helm templates in helm/devops-demo/templates/.
```

### GitOps Advanced Patterns

```
Enhance GitOps setup with ArgoCD:
1. Implement ApplicationSet for multi-environment deployments
2. Add Kustomize overlays for environment-specific configs
3. Configure automated image updater
4. Implement progressive delivery with Argo Rollouts
5. Add sync waves for ordered deployments
6. Configure webhook-based sync triggers

Update argocd/ directory with advanced configurations.
```

### Cost Optimization

```
Implement cost optimization strategies:
1. Add pod autoscaling based on custom metrics
2. Implement cluster autoscaling
3. Use spot instances for non-critical workloads
4. Add resource recommendations based on actual usage
5. Implement pod scheduling with node affinity for cost optimization
6. Add cost monitoring dashboards

Provide Kubernetes manifests and analysis tools.
```

---

## Quick Task Prompts

### Quick Fixes

```
Quick fix: Add request ID tracking to all Flask endpoints
```

```
Quick fix: Update Python dependencies to latest secure versions
```

```
Quick fix: Add health check endpoint that validates all dependencies
```

```
Quick fix: Implement graceful shutdown handling in Flask app
```

### Code Review Prompts

```
Review app/main.py for:
- Security vulnerabilities
- Performance issues
- Code quality problems
- Missing error handling
- Best practices violations

Provide specific recommendations with code examples.
```

```
Review Dockerfile for:
- Security best practices
- Image size optimization
- Build performance
- Layer caching efficiency
- Multi-platform support

Suggest improvements with reasoning.
```

```
Review Helm chart for:
- Kubernetes best practices
- Security configurations
- Resource management
- High availability setup
- Production readiness

Provide detailed feedback and examples.
```

---

## Learning Prompts

### Understanding the Codebase

```
Explain the complete architecture of this DevOps demo project:
- Application structure
- Docker containerization approach
- Kubernetes deployment strategy
- CI/CD pipeline flow
- GitOps implementation with ArgoCD

Make it comprehensive but easy to understand.
```

### Best Practices Explanation

```
Explain the DevOps best practices implemented in this project:
- Multi-stage Docker builds
- GitFlow branching strategy
- Automated testing in CI/CD
- Infrastructure as Code with Helm
- GitOps with ArgoCD

Include why each practice is important.
```

---

## Template Prompts

### Creating Similar Projects

```
Using this project as a template, create a similar setup for:
- [Language: Node.js/Python/Go]
- [Framework: Express/FastAPI/Gin]
- [Database: PostgreSQL/MongoDB/Redis]

Maintain the same DevOps structure and best practices.
```

### Extending the Project

```
Extend this project to include:
- [Feature: Authentication/Authorization]
- [Service: Database/Cache/Queue]
- [Tool: Monitoring/Logging/Tracing]

Follow existing patterns and conventions.
```

---

## Tips for Using These Prompts

1. **Be Specific**: Add context about your specific issue or requirement
2. **Reference Files**: Mention specific files and line numbers when relevant
3. **Provide Context**: Explain what you've already tried
4. **Combine Prompts**: Mix and match prompts for complex tasks
5. **Iterate**: Refine prompts based on initial responses
6. **Ask for Explanations**: Add "Explain why" to understand the reasoning

## Custom Prompt Template

```
Task: [Describe what you want to accomplish]

Context: [Provide relevant background]

Requirements:
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

Constraints:
- [Constraint 1]
- [Constraint 2]

Expected Outcome: [Describe the desired result]

Files to Modify: [List specific files]

Testing: [Describe testing approach]
```

---

For project-specific context, always refer to `.github/copilot-instructions.md`.
