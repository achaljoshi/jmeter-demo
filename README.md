# QForge Demo - JMeter Performance Tests

Sample JMeter automation framework used by QForge Automation demos.

## Stack

- Apache JMeter via Maven
- `jmeter-maven-plugin`
- GitHub Actions `workflow_dispatch`
- JTL results + HTML dashboard artifacts

## Test Plans

- `src/test/jmeter/customer-search-load.jmx` - lightweight HTTP performance smoke test against `https://httpbin.org`.

## Run locally

```bash
mvn -B verify
```

Run a single test plan by name:

```bash
mvn -B verify -Djmeter.testPlan=customer-search-load
```

Override load settings:

```bash
mvn -B verify -Dthreads=5 -Drampup=5 -Dloops=3
```

## Reports

- JTL results: `target/jmeter/results/`
- HTML dashboard: `target/jmeter/reports/`

## GitHub Actions

Workflow: `.github/workflows/qforge-jmeter.yml`

Inputs:

- `test_name`: optional test plan name, for example `customer-search-load`
- `threads`: virtual users
- `rampup`: ramp-up seconds
- `loops`: iterations per user