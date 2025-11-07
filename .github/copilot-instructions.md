# GitHub Copilot Custom Instructions for DevOps-Demo-Project

This file provides context-aware instructions for GitHub Copilot to assist with this DevOps demonstration project.

## Project Overview

This is a comprehensive DevOps demonstration project featuring:

- **Python Flask REST API** with health checks and monitoring endpoints
- **Docker** multi-stage builds optimized for production
- **Kubernetes** deployment using Helm charts with HPA
- **GitOps** with ArgoCD for automated deployments
- **CI/CD** pipelines via GitHub Actions
- **GitFlow** branching workflow with automated validation

## Code Style & Standards

### Python

- Use **Python 3.11+** features
- Follow **PEP 8** style guide
- Use **type hints** for function parameters and returns
- Write **docstrings** for all public functions and classes
- Prefer **f-strings** for string formatting
- Use **pathlib** for file operations
- Keep functions **small and focused** (max 20-30 lines)

### Testing

- Write tests using **pytest**
- Aim for **>80% code coverage**
- Use **fixtures** for test setup
- Follow **AAA pattern** (Arrange, Act, Assert)
- Name tests: `test_<feature>_<scenario>_<expected_outcome>`

### Docker

- Use **multi-stage builds** to minimize image size
- Run containers as **non-root user** (UID 1000)
- Implement **read-only root filesystem** where possible
- Use **.dockerignore** to exclude unnecessary files
- Always include **HEALTHCHECK** directives
- Optimize **layer caching** for faster builds

### Kubernetes

- Use **Helm charts** for all deployments
- Define **resource limits and requests**
- Implement **liveness and readiness probes**
- Use **HPA** for automatic scaling
- Follow **pod security policies**
- Use **labels and selectors** consistently

### Git Workflow

- Follow **GitFlow branching model**
- Use **conventional commits** format: `type(scope): description`
- Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`
- Branch naming:
  - `feature/description`
  - `bugfix/description`
  - `release/x.y.z`
  - `hotfix/description`

## Project Structure Context

```
DevOps-Demo-Project/
├── app/                    # Flask application
│   ├── __init__.py
│   └── main.py            # Main application file
├── tests/                  # Test suite
│   └── test_main.py       # Unit tests
├── docker/                 # Docker configuration
│   ├── Dockerfile         # Multi-stage build
│   └── docker-compose.yml
├── helm/                   # Helm charts
│   └── devops-demo/
│       ├── Chart.yaml
│       ├── values.yaml
│       └── templates/     # K8s manifests
├── argocd/                 # ArgoCD config
├── .github/workflows/      # GitHub Actions
│   ├── ci.yml             # Build & test
│   ├── cd.yml             # Deploy
│   ├── release.yml        # Release automation
│   └── gitflow.yml        # Branch validation
└── scripts/                # Setup scripts
```

## Common Tasks & Patterns

### Adding a New API Endpoint

When adding new endpoints to Flask:

1. Add route handler in `app/main.py`
2. Include proper error handling
3. Return JSON responses with consistent format
4. Add corresponding tests in `tests/test_main.py`
5. Update `docs/API.md` documentation
6. Include health/monitoring considerations

Example pattern:

```python
@app.route('/api/endpoint')
def endpoint():
    """Endpoint description"""
    try:
        # Logic here
        return jsonify({'data': result}), 200
    except Exception as e:
        return jsonify({'error': str(e)}), 500
```

### Modifying Helm Charts

When updating Kubernetes deployments:

1. Edit `helm/devops-demo/values.yaml` for configuration
2. Update templates in `helm/devops-demo/templates/`
3. Increment chart version in `Chart.yaml`
4. Test with: `helm lint helm/devops-demo`
5. Verify with: `helm template devops-demo helm/devops-demo`
6. Update `docs/DEPLOYMENT.md` if needed

### CI/CD Pipeline Changes

When modifying workflows:

1. Edit appropriate file in `.github/workflows/`
2. Use `act` for local testing if available
3. Follow existing job structure and naming
4. Add proper error handling
5. Use caching for dependencies
6. Consider security implications

### Adding Dependencies

For Python dependencies:

1. Add to `pyproject.toml` under appropriate section
2. Run: `uv pip install -e ".[dev]"`
3. Update Dockerfile if runtime dependency
4. Test in isolated environment
5. Check for security vulnerabilities

## Kubernetes Deployment Patterns

### Deployment Strategy

- Use **rolling updates** with maxSurge: 1, maxUnavailable: 0
- Set appropriate **replica counts** (min 2 for HA)
- Configure **pod disruption budgets**
- Use **anti-affinity rules** for pod distribution

### Service Configuration

- ClusterIP for internal services
- LoadBalancer/Ingress for external access
- Define clear port naming conventions
- Use service mesh if available

### ConfigMaps & Secrets

- Store non-sensitive config in ConfigMaps
- Store credentials in Secrets (encrypted at rest)
- Mount as volumes or environment variables
- Avoid hardcoding in images

## Security Best Practices

### Container Security

- Run as **non-root user**
- Use **minimal base images** (alpine, distroless)
- Scan images for vulnerabilities
- Implement **read-only root filesystem**
- Drop unnecessary capabilities

### API Security

- Implement **rate limiting**
- Use **authentication/authorization** for sensitive endpoints
- Validate and sanitize all inputs
- Use HTTPS/TLS in production
- Implement CORS policies

### Secrets Management

- Never commit secrets to Git
- Use Kubernetes Secrets or external secret managers
- Rotate credentials regularly
- Use least privilege access

## GitFlow Workflow Rules

### Branch Targets

- `feature/*` → merge to `develop`
- `bugfix/*` → merge to `develop`
- `release/*` → merge to `main` AND `develop`
- `hotfix/*` → merge to `main` AND `develop`

### Version Bumping

- **Major** (x.0.0): Breaking changes
- **Minor** (0.x.0): New features (backward compatible)
- **Patch** (0.0.x): Bug fixes

### Release Process

1. Create `release/x.y.z` from `develop`
2. Update version in all files
3. Update CHANGELOG.md
4. Create PR to `main`
5. After merge, tag is auto-created
6. Changes merge back to `develop`

## Monitoring & Observability

### Logging

- Use structured logging (JSON format)
- Include correlation IDs
- Log at appropriate levels
- Don't log sensitive data

### Metrics

- Expose Prometheus-compatible metrics
- Track: request rate, error rate, duration
- Monitor resource usage
- Set up alerts for anomalies

### Health Checks

- `/health` - Liveness probe
- `/ready` - Readiness probe
- Both should be fast (<1s)
- Include dependency checks in readiness

## Testing Strategy

### Unit Tests

- Test individual functions/methods
- Mock external dependencies
- Fast execution (<100ms per test)
- Aim for >80% coverage

### Integration Tests

- Test component interactions
- Use test containers when possible
- Validate API contracts
- Test error scenarios

### End-to-End Tests

- Test complete user workflows
- Run in CI/CD pipeline
- Use production-like environment
- Validate critical paths only

## Documentation Requirements

When making changes, update:

1. **Code comments** - Why, not what
2. **API.md** - For new/changed endpoints
3. **README.md** - For user-facing changes
4. **DEPLOYMENT.md** - For infrastructure changes
5. **CHANGELOG.md** - All notable changes

## Performance Considerations

### Application Performance

- Use connection pooling
- Implement caching where appropriate
- Optimize database queries
- Use async/await for I/O operations
- Profile before optimizing

### Resource Management

- Set appropriate CPU/memory limits
- Use HPA for auto-scaling
- Monitor and adjust based on metrics
- Implement circuit breakers

## Troubleshooting Guides

### Common Issues

**Pod CrashLoopBackOff:**

- Check logs: `kubectl logs <pod> -n devops-demo`
- Verify resource limits
- Check liveness/readiness probes
- Validate configuration

**Image Pull Errors:**

- Verify image exists
- Check image pull secrets
- Validate registry credentials
- Check network connectivity

**ArgoCD Sync Failures:**

- Check application status
- Validate Helm chart syntax
- Review ArgoCD logs
- Verify Git repository access

## AI Pair Programming Tips

When working with this project:

1. **Context is key** - Reference specific files and line numbers
2. **Test-driven** - Write tests first, then implementation
3. **Security-focused** - Always consider security implications
4. **Performance-aware** - Consider resource usage and optimization
5. **Documentation** - Update docs alongside code changes

## Quick Reference Commands

### Local Development

```bash
# Setup
source .venv/bin/activate

# Run app
python app/main.py
gunicorn --bind 0.0.0.0:8080 app.main:app

# Tests
pytest tests/ -v --cov=app
```

### Docker

```bash
# Build
docker build -f docker/Dockerfile -t devops-demo:latest .

# Run
docker run -p 8080:8080 devops-demo:latest
docker-compose -f docker/docker-compose.yml up
```

### Kubernetes

```bash
# Deploy
helm install devops-demo helm/devops-demo -n devops-demo

# Debug
kubectl get pods -n devops-demo
kubectl logs -f deployment/devops-demo -n devops-demo
kubectl describe pod <pod-name> -n devops-demo
```

### Git

```bash
# Feature
git checkout develop
git checkout -b feature/my-feature

# Release
git checkout develop
git checkout -b release/1.0.0
```

## Additional Context

- **Python Version**: 3.11+
- **Flask Version**: 3.0.0+
- **Kubernetes Version**: 1.28+
- **Helm Version**: 3.12+
- **Docker Version**: 20.10+

For detailed information, refer to:

- [README.md](../README.md) - Main documentation
- [API.md](../docs/API.md) - API reference
- [DEPLOYMENT.md](../docs/DEPLOYMENT.md) - Deployment guide
- [GITFLOW.md](../docs/GITFLOW.md) - Branching strategy
