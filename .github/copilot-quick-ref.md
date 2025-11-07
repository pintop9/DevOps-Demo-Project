# GitHub Copilot Quick Reference for DevOps-Demo-Project

Quick reference guide for common GitHub Copilot interactions in this project.

## 🎯 Quick Start

### Activate Project Context
```
Load context from .github/copilot-instructions.md and help me with [task]
```

### Get Project Overview
```
Explain the architecture and structure of this DevOps demo project
```

---

## 💡 Common One-Liners

### Development

```bash
# Add a new Flask endpoint
"Add POST /api/users endpoint with validation and tests"

# Refactor code
"Refactor app/main.py to use blueprints for better organization"

# Fix bug
"Fix the health check endpoint returning 500 on startup"

# Add feature
"Add request logging middleware with correlation IDs"
```

### Testing

```bash
# Write tests
"Write comprehensive tests for the /api/echo endpoint"

# Improve coverage
"Add tests to increase coverage of app/main.py to 90%"

# Integration tests
"Create integration tests for all API endpoints"

# Mock dependencies
"Add fixtures for mocking external dependencies"
```

### Docker

```bash
# Optimize Dockerfile
"Reduce Docker image size in docker/Dockerfile to under 100MB"

# Multi-stage build
"Improve multi-stage build caching in Dockerfile"

# Security scan
"Add vulnerability scanning to Dockerfile build process"

# Multi-platform
"Ensure docker/Dockerfile supports linux/amd64 and linux/arm64"
```

### Kubernetes

```bash
# Resource tuning
"Optimize resource requests/limits in helm/devops-demo/values.yaml"

# Add feature
"Add PostgreSQL as a dependency in Helm chart"

# Security hardening
"Implement pod security policies in Helm templates"

# Monitoring
"Add Prometheus ServiceMonitor to Helm chart"
```

### CI/CD

```bash
# Fix pipeline
"Debug failing test job in .github/workflows/ci.yml"

# Optimize
"Speed up CI build time by adding better caching"

# Add stage
"Add security scanning stage to CI pipeline"

# Deploy automation
"Create staging deployment workflow"
```

### Documentation

```bash
# API docs
"Generate OpenAPI spec from Flask endpoints"

# Update README
"Update README.md with new feature documentation"

# Troubleshooting guide
"Create troubleshooting guide for common Kubernetes issues"

# Architecture diagram
"Create Mermaid diagram of the CI/CD pipeline"
```

---

## 🔍 Debugging Shortcuts

```bash
# Kubernetes pod issues
"Pod is in CrashLoopBackOff, help me debug"

# Performance issues
"API response time is 2s, help me optimize"

# Memory leak
"App memory usage is growing, help find the leak"

# Build failures
"Docker build is failing at pip install step"

# Test failures
"Test test_health_endpoint is failing intermittently"
```

---

## 📋 Templates

### New API Endpoint Template
```
Create a new API endpoint:

Path: /api/[endpoint]
Method: [GET/POST/PUT/DELETE]
Purpose: [Description]

Requirements:
- Input validation
- Error handling
- Logging
- Tests (>80% coverage)
- API documentation

Follow patterns in app/main.py
```

### New Kubernetes Resource Template
```
Add Kubernetes resource to helm/devops-demo/:

Resource: [Deployment/Service/ConfigMap/Secret]
Purpose: [Description]

Requirements:
- Security best practices
- Resource limits
- Health checks
- Labels and annotations
- Documentation

Follow existing templates
```

### New GitHub Workflow Template
```
Create GitHub Actions workflow:

Purpose: [Description]
Trigger: [push/pull_request/schedule]

Jobs:
1. [Job 1]
2. [Job 2]
3. [Job 3]

Requirements:
- Caching
- Error handling
- Notifications
- Security scanning

Reference existing workflows in .github/workflows/
```

---

## 🎨 Code Generation Patterns

### Flask Endpoint Pattern
```python
@app.route('/api/<resource>', methods=['<METHOD>'])
def <function_name>():
    """<Docstring>"""
    try:
        # Validation
        # Logic
        return jsonify({'data': result}), 200
    except Exception as e:
        return jsonify({'error': str(e)}), 500
```

### Pytest Test Pattern
```python
def test_<feature>_<scenario>_<expected>(<fixtures>):
    """Test <description>"""
    # Arrange
    <setup>
    
    # Act
    <execute>
    
    # Assert
    <verify>
```

### Kubernetes Manifest Pattern
```yaml
apiVersion: <api-version>
kind: <kind>
metadata:
  name: {{ include "devops-demo.fullname" . }}
  labels:
    {{- include "devops-demo.labels" . | nindent 4 }}
spec:
  <spec>
```

---

## 🚀 Context-Aware Prompts

### With File Context
```
# Looking at app/main.py
"Add caching to this endpoint"

# Looking at Dockerfile
"Optimize this for production"

# Looking at values.yaml
"Add PostgreSQL configuration"

# Looking at ci.yml
"Add security scanning here"
```

### With Selection Context
```
# Select code block
"Refactor this to be more testable"
"Add error handling to this"
"Write tests for this function"
"Explain what this code does"
```

### With Error Context
```
# When seeing error in terminal
"Fix this error"
"Explain this error"
"Why is this failing?"
```

---

## 🛠️ Workflow Shortcuts

### Feature Development Flow
```
1. "Create feature branch for [feature]"
2. "Implement [feature] following project patterns"
3. "Write tests for [feature]"
4. "Update documentation for [feature]"
5. "Review code for potential issues"
```

### Bug Fix Flow
```
1. "Analyze this error: [error message]"
2. "Suggest root cause and fix"
3. "Implement fix with tests"
4. "Add regression test"
5. "Update relevant documentation"
```

### Deployment Flow
```
1. "Review Kubernetes manifests for production readiness"
2. "Check resource limits and scaling configuration"
3. "Verify health checks and monitoring"
4. "Create deployment checklist"
5. "Generate rollback plan"
```

---

## 🎓 Learning Prompts

### Understanding Code
```
"Explain how the Flask app is structured"
"What does this Dockerfile do?"
"Explain the Helm chart template logic"
"How does the CI/CD pipeline work?"
```

### Best Practices
```
"What are best practices for Flask error handling?"
"Explain Docker multi-stage build benefits"
"What are Kubernetes security best practices?"
"Explain GitFlow workflow advantages"
```

### Troubleshooting
```
"Common causes of CrashLoopBackOff?"
"How to debug slow API responses?"
"What tools to use for Kubernetes debugging?"
"How to analyze Docker build performance?"
```

---

## 📊 Analysis Prompts

### Code Quality
```
"Analyze app/main.py for code quality issues"
"Review test coverage and suggest improvements"
"Identify security vulnerabilities in the codebase"
"Find performance bottlenecks"
```

### Infrastructure
```
"Analyze Kubernetes resource usage"
"Review Helm chart for production readiness"
"Evaluate Docker image security"
"Assess CI/CD pipeline efficiency"
```

### Documentation
```
"Check documentation completeness"
"Identify missing API documentation"
"Review runbook coverage"
"Suggest documentation improvements"
```

---

## 💻 Command Assistance

### Get Commands
```
"kubectl command to check pod logs"
"helm command to upgrade release"
"docker command to build multi-platform image"
"git command for GitFlow release"
```

### Generate Scripts
```
"Generate bash script to deploy to staging"
"Create Python script to test all endpoints"
"Write shell script to cleanup old Docker images"
"Generate script to validate Helm charts"
```

---

## 🎯 Goal-Oriented Prompts

### Improve Performance
```
"Make the API 50% faster"
"Reduce Docker image size by half"
"Optimize Kubernetes resource usage"
"Speed up CI/CD pipeline"
```

### Enhance Security
```
"Make the application more secure"
"Harden Kubernetes deployment"
"Implement security scanning"
"Add authentication to API"
```

### Increase Reliability
```
"Make the app more resilient"
"Add comprehensive monitoring"
"Implement circuit breakers"
"Create disaster recovery plan"
```

---

## 🔄 Iterative Prompts

### Initial Request
```
"Add user authentication to the Flask app"
```

### Follow-up
```
"Use JWT tokens instead"
"Add refresh token logic"
"Implement token rotation"
"Add rate limiting"
"Write tests for authentication"
```

---

## 📝 Documentation Requests

### Auto-Generate
```
"Generate API documentation from code"
"Create architecture diagram"
"Generate changelog from commits"
"Create deployment runbook"
```

### Update
```
"Update README with new features"
"Add troubleshooting section to docs"
"Update API docs with new endpoints"
"Refresh deployment guide"
```

---

## 🎪 Advanced Use Cases

### Multi-File Changes
```
"Add database support to the entire project"
"Implement distributed tracing across all services"
"Add comprehensive monitoring stack"
"Set up multi-region deployment"
```

### Complex Refactoring
```
"Refactor app to use microservices architecture"
"Migrate from Flask to FastAPI"
"Convert synchronous code to async"
"Implement event-driven architecture"
```

### Infrastructure as Code
```
"Generate Terraform for AWS deployment"
"Create complete observability stack"
"Implement service mesh with Istio"
"Add complete security hardening"
```

---

## 🌟 Pro Tips

1. **Be Specific**: "Add logging to /health endpoint" > "improve logging"
2. **Provide Context**: Reference specific files and line numbers
3. **Iterate**: Start simple, then add requirements
4. **Use Examples**: "Like in test_health_endpoint" helps
5. **State Constraints**: "Without external dependencies" or "Using only stdlib"
6. **Ask for Explanation**: Add "and explain why" to learn
7. **Request Alternatives**: "Show 3 different approaches"
8. **Batch Related Tasks**: "Add endpoint, tests, and docs"

---

## 🎨 Customization

### Personal Shortcuts
Add your frequently used prompts:

```
# Your custom prompt 1
"[Your frequently used task]"

# Your custom prompt 2
"[Your common workflow]"

# Your custom prompt 3
"[Your specific need]"
```

---

## 📚 Reference Files

When working on this project, reference:

- **Instructions**: `.github/copilot-instructions.md`
- **Prompts Library**: `.github/copilot-prompts.md`
- **Chat Modes**: `.github/copilot-chat-modes.md`
- **This Guide**: `.github/copilot-quick-ref.md`

---

## 🆘 When Stuck

```
"I'm trying to [goal] but getting [error/issue]. 
I've tried [what you tried].
Context: [relevant context]
Help me troubleshoot systematically."
```

---

## 📞 Getting Help

```
"I don't understand [concept] in this project"
"Explain the relationship between [component A] and [component B]"
"What's the best way to [task] in this project?"
"Show me examples of [pattern] in the codebase"
```

---

**Quick Start**: Copy any prompt above and customize it for your needs!

For detailed prompts, see `.github/copilot-prompts.md`
For specialized modes, see `.github/copilot-chat-modes.md`
