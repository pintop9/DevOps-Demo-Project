# GitHub Copilot Chat Modes for DevOps-Demo-Project

Specialized chat mode configurations for different DevOps scenarios and roles.

## Table of Contents

- [Developer Mode](#developer-mode)
- [DevOps Engineer Mode](#devops-engineer-mode)
- [Security Engineer Mode](#security-engineer-mode)
- [SRE Mode](#sre-mode)
- [Code Reviewer Mode](#code-reviewer-mode)
- [Documentation Writer Mode](#documentation-writer-mode)
- [Debugger Mode](#debugger-mode)
- [Performance Optimizer Mode](#performance-optimizer-mode)

---

## Developer Mode

**Purpose**: Building and testing application features

### Activation Prompt
```
Act as a senior Python developer working on a Flask microservice.
Focus on clean code, testing, and following the project's conventions.
Reference app/main.py and tests/test_main.py for existing patterns.
Follow PEP 8 and use type hints. Prioritize testability and maintainability.
```

### Common Tasks

#### Feature Development
```
I need to add a new feature to the Flask app:
[Describe feature]

Please:
1. Implement the feature following existing patterns in app/main.py
2. Write comprehensive tests in tests/test_main.py
3. Update API documentation in docs/API.md
4. Ensure backward compatibility
5. Add appropriate logging and error handling
```

#### Refactoring
```
Refactor app/main.py to:
- Improve code organization and modularity
- Extract reusable components
- Enhance error handling
- Improve type hints and documentation
- Maintain all existing functionality and tests
```

#### Test Writing
```
Generate comprehensive pytest tests for [function/endpoint]:
- Happy path scenarios
- Edge cases and boundaries
- Error conditions
- Performance considerations
- Use appropriate fixtures from tests/conftest.py
```

---

## DevOps Engineer Mode

**Purpose**: Infrastructure, deployment, and CI/CD pipeline management

### Activation Prompt
```
Act as a DevOps engineer specializing in Kubernetes, Docker, and CI/CD.
Focus on automation, reliability, and infrastructure as code.
Reference helm/, docker/, and .github/workflows/ for existing patterns.
Prioritize security, scalability, and maintainability.
```

### Common Tasks

#### Kubernetes Configuration
```
Help me with Kubernetes configuration for [component]:

Context: [Describe the component/service]

Requirements:
- High availability setup
- Appropriate resource limits
- Health checks and monitoring
- Security best practices
- Production-ready configuration

Update helm/devops-demo/ accordingly.
```

#### CI/CD Pipeline
```
I need to enhance the CI/CD pipeline to:
[List requirements]

Current workflows: .github/workflows/ci.yml, cd.yml

Please:
1. Analyze current pipeline
2. Suggest improvements
3. Implement changes
4. Add proper error handling
5. Optimize for speed and reliability
```

#### Docker Optimization
```
Optimize docker/Dockerfile for:
- Smaller image size
- Faster builds
- Better caching
- Enhanced security
- Multi-platform support

Current image size: [X]MB
Target: <100MB
```

---

## Security Engineer Mode

**Purpose**: Security hardening, vulnerability scanning, and compliance

### Activation Prompt
```
Act as a security engineer conducting a security review.
Focus on identifying vulnerabilities, implementing security best practices,
and ensuring compliance with security standards.
Analyze code, containers, and Kubernetes configurations for security issues.
```

### Common Tasks

#### Security Audit
```
Perform a comprehensive security audit of:
- Application code (app/)
- Docker configuration (docker/)
- Kubernetes manifests (helm/)
- CI/CD pipelines (.github/workflows/)

Identify:
1. Security vulnerabilities
2. Misconfigurations
3. Compliance issues
4. Credential exposure risks
5. Supply chain security concerns

Provide specific recommendations with severity levels.
```

#### Vulnerability Remediation
```
I have the following security scan results:
[Paste scan results]

Please:
1. Analyze each vulnerability
2. Assess risk and impact
3. Provide remediation steps
4. Suggest preventive measures
5. Update relevant files
```

#### Secret Management
```
Implement secure secret management:
1. Audit current secret handling
2. Integrate with [External Secrets Operator/Vault/AWS Secrets Manager]
3. Update Helm charts for external secrets
4. Implement secret rotation
5. Remove hardcoded credentials

Update helm/devops-demo/ and document the process.
```

---

## SRE Mode

**Purpose**: Reliability, observability, and incident response

### Activation Prompt
```
Act as a Site Reliability Engineer focused on system reliability,
observability, and incident management. Emphasize monitoring, alerting,
SLOs, error budgets, and operational excellence.
```

### Common Tasks

#### Observability Setup
```
Implement comprehensive observability:

Components:
- Metrics (Prometheus)
- Logs (Loki/ELK)
- Traces (Tempo/Jaeger)
- Dashboards (Grafana)

For the Flask app and Kubernetes deployment.

Include:
1. Instrumentation code
2. Kubernetes manifests
3. Alert rules
4. Runbooks
```

#### SLO Definition
```
Define SLOs and SLIs for the devops-demo service:

Service characteristics:
- API service with [X] endpoints
- Expected traffic: [Y] req/s
- User-facing: [Yes/No]

Create:
1. SLI definitions
2. SLO targets
3. Error budgets
4. Alert policies
5. Monitoring dashboards
```

#### Incident Response
```
I'm experiencing an incident:
Symptoms: [Describe symptoms]
Impact: [User impact]
Duration: [How long]

Help me:
1. Diagnose the root cause
2. Provide immediate mitigation steps
3. Suggest monitoring commands
4. Create post-incident action items
5. Update runbooks
```

---

## Code Reviewer Mode

**Purpose**: Code review and quality assurance

### Activation Prompt
```
Act as a thorough code reviewer conducting a detailed code review.
Focus on code quality, best practices, potential bugs, security issues,
performance concerns, and maintainability. Be constructive and educational.
```

### Common Tasks

#### Pull Request Review
```
Review this pull request:

Changes: [Describe changes or paste diff]

Files modified:
- [List files]

Review for:
1. Code quality and style
2. Best practices adherence
3. Security vulnerabilities
4. Performance implications
5. Test coverage
6. Documentation completeness

Provide specific, actionable feedback with examples.
```

#### Architecture Review
```
Review the architecture design for:
[Describe new feature/component]

Proposed design:
[Design details]

Evaluate:
1. Alignment with existing architecture
2. Scalability considerations
3. Security implications
4. Complexity and maintainability
5. Alternative approaches

Provide recommendations and trade-offs.
```

#### Test Coverage Review
```
Review test coverage for:
[Component/Module]

Current coverage: [X]%
Test files: [List]

Analyze:
1. Coverage gaps
2. Test quality and effectiveness
3. Edge cases missed
4. Integration test needs
5. Test maintainability

Suggest specific tests to add.
```

---

## Documentation Writer Mode

**Purpose**: Creating and maintaining technical documentation

### Activation Prompt
```
Act as a technical writer creating clear, comprehensive documentation.
Focus on user perspective, step-by-step instructions, examples,
and troubleshooting guides. Make complex topics accessible.
```

### Common Tasks

#### API Documentation
```
Create comprehensive API documentation for:
[Endpoint/Service]

Include:
1. Endpoint description and purpose
2. Request/response schemas
3. Authentication requirements
4. Example requests (curl, Python, JavaScript)
5. Error codes and meanings
6. Rate limiting info
7. Versioning details

Output in Markdown format for docs/API.md.
```

#### Runbook Creation
```
Create an operational runbook for:
[Service/Component]

Include:
1. Service overview
2. Architecture diagram
3. Dependencies
4. Monitoring and alerts
5. Common issues and solutions
6. Escalation procedures
7. Useful commands and queries

Target audience: On-call engineers.
```

#### Tutorial Writing
```
Write a step-by-step tutorial for:
[Task/Feature]

Audience: [Beginner/Intermediate/Advanced]

Include:
1. Prerequisites
2. Setup instructions
3. Detailed steps with commands
4. Expected outputs
5. Troubleshooting section
6. Best practices
7. Further resources
```

---

## Debugger Mode

**Purpose**: Troubleshooting and problem-solving

### Activation Prompt
```
Act as an expert debugger helping troubleshoot production issues.
Use systematic debugging approaches. Focus on root cause analysis,
not just symptoms. Provide diagnostic commands and investigation steps.
```

### Common Tasks

#### Application Debugging
```
Debug this issue in the Flask application:

Problem: [Describe the issue]
Error messages: [Paste errors]
Steps to reproduce: [List steps]
Environment: [Dev/Staging/Prod]

Help me:
1. Analyze the error
2. Identify root cause
3. Provide diagnostic steps
4. Suggest fixes
5. Recommend prevention measures
```

#### Kubernetes Troubleshooting
```
Troubleshoot Kubernetes deployment issue:

Problem: [Issue description]
Pod status: [CrashLoopBackOff/ImagePullBackOff/etc]
Namespace: devops-demo

Provide:
1. Diagnostic kubectl commands
2. Log analysis
3. Configuration review
4. Root cause identification
5. Fix implementation
6. Prevention strategies
```

#### Performance Investigation
```
Investigate performance degradation:

Symptoms:
- [Symptom 1]
- [Symptom 2]

Metrics observed:
- [Metric data]

Timeline: [When it started]

Help me:
1. Identify bottlenecks
2. Analyze system resources
3. Review application code
4. Suggest optimizations
5. Implement monitoring
```

---

## Performance Optimizer Mode

**Purpose**: Performance analysis and optimization

### Activation Prompt
```
Act as a performance optimization expert. Analyze code and infrastructure
for performance bottlenecks. Use profiling, benchmarking, and metrics.
Focus on measurable improvements and trade-offs.
```

### Common Tasks

#### Application Performance
```
Optimize performance of:
[Component/Endpoint]

Current metrics:
- Response time: [X]ms
- Throughput: [Y] req/s
- Resource usage: [CPU/Memory]

Goals:
- Target response time: [Z]ms
- Target throughput: [W] req/s

Analyze and optimize:
1. Code-level optimizations
2. Database queries (if applicable)
3. Caching strategies
4. Async/parallel processing
5. Resource utilization

Provide before/after benchmarks.
```

#### Infrastructure Optimization
```
Optimize Kubernetes deployment for cost and performance:

Current setup:
- Replicas: [N]
- CPU request/limit: [X]
- Memory request/limit: [Y]
- Current cost: [Z]

Goals:
- Maintain performance
- Reduce cost by [X]%
- Improve resource utilization

Analyze:
1. Resource usage patterns
2. HPA configuration
3. Node sizing
4. Scheduling optimization
5. Cost/performance trade-offs
```

#### Build Performance
```
Optimize CI/CD build performance:

Current build time: [X] minutes

Optimize:
1. Docker build stages
2. Dependency caching
3. Parallel job execution
4. Test execution time
5. Artifact handling

Target: <[Y] minutes

Provide specific improvements with expected time savings.
```

---

## Specialized Task Modes

### Migration Mode

```
Act as a migration specialist helping with:
- Language/framework migrations
- Platform migrations (cloud providers)
- Database migrations
- Kubernetes version upgrades
- Breaking dependency updates

Provide step-by-step migration plans with rollback strategies.
```

#### Example Usage
```
Plan migration from Flask 2.x to Flask 3.x:

Current setup: [Details]

Provide:
1. Breaking changes analysis
2. Migration steps
3. Testing strategy
4. Rollback plan
5. Monitoring during migration
```

### Disaster Recovery Mode

```
Act as a disaster recovery expert. Focus on backup strategies,
recovery procedures, RTO/RPO requirements, and disaster scenarios.
```

#### Example Usage
```
Create disaster recovery plan for devops-demo:

Requirements:
- RTO: [X] minutes
- RPO: [Y] minutes
- Critical data: [List]

Provide:
1. Backup strategy
2. Recovery procedures
3. Failover mechanisms
4. DR testing plan
5. Documentation
```

### Compliance Mode

```
Act as a compliance expert ensuring adherence to standards like
SOC2, HIPAA, PCI-DSS, or GDPR. Focus on controls, audit trails,
and compliance documentation.
```

#### Example Usage
```
Ensure SOC2 compliance for devops-demo:

Requirements:
- Access controls
- Audit logging
- Data encryption
- Change management
- Monitoring and alerting

Audit and provide compliance checklist with implementation steps.
```

---

## Multi-Mode Workflows

### End-to-End Feature Development

```
Workflow combining multiple modes:

1. Developer Mode: Implement feature
2. Code Reviewer Mode: Review implementation
3. DevOps Engineer Mode: Update deployment configs
4. Security Engineer Mode: Security review
5. Documentation Writer Mode: Update docs
6. SRE Mode: Add monitoring

For feature: [Describe feature]

Coordinate across all modes to deliver production-ready feature.
```

### Production Incident Workflow

```
Incident response workflow:

1. Debugger Mode: Diagnose issue
2. SRE Mode: Assess impact and SLO burn
3. DevOps Engineer Mode: Implement fix
4. Performance Optimizer Mode: Optimize if needed
5. Documentation Writer Mode: Update runbooks

Incident: [Describe incident]

Execute workflow systematically.
```

---

## Mode Switching Tips

1. **Be Explicit**: Clearly state which mode you want to activate
2. **Provide Context**: Share relevant files and current state
3. **State Goals**: Define what you want to achieve
4. **Switch Deliberately**: Change modes when shifting focus
5. **Combine When Needed**: Use multi-mode workflows for complex tasks

## Example Mode Activation

```
[Mode: DevOps Engineer]

Task: Update Helm chart for multi-region deployment

Context:
- Current setup: Single region
- Target: 3 regions (us-east, us-west, eu-central)
- Requirements: Active-active, shared database

Please analyze current helm/devops-demo/ and provide
multi-region deployment strategy with updated manifests.
```

---

## Custom Mode Template

```
[Mode: Your Custom Mode]

Role: [Define the role/expertise]

Focus Areas:
- [Area 1]
- [Area 2]
- [Area 3]

Task: [Describe what you need]

Context: [Provide background]

Deliverables:
1. [Expected output 1]
2. [Expected output 2]
3. [Expected output 3]
```

---

For project context and conventions, always refer to:
- `.github/copilot-instructions.md` - Project conventions
- `.github/copilot-prompts.md` - Curated prompts library
