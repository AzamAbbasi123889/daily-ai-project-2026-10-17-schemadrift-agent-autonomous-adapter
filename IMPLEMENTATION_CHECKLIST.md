# Implementation Checklist

Build the application yourself using `PROJECT_BRIEF.md`.

## Initial setup

- [ ] Read the project specification.
- [ ] Review the architecture and data model.
- [ ] Create a Python virtual environment.
- [ ] Install and pin the required dependencies.
- [ ] Configure credentials through environment variables.
- [ ] Review the data privacy and security requirements.

## Project acceptance criteria

- [ ] Rejects malformed payloads with HTTP 422 while immediately capturing the raw JSON and validation error stack in PostgreSQL
- [ ] Produces an automated DeepDiff breakdown identifying altered field paths, type mismatches, and missing mandatory keys in < 100ms
- [ ] Agent has access to tools: get_schema_diff, fetch_historical_samples, run_sandbox_transformation, and evaluate_assertions
- [ ] Agent successfully resolves schema discrepancies through iterative error feedback within a maximum of 3 tool-execution cycles
- [ ] Must verify 100% schema compliance across both the failing drifted payload and previous historical records
- [ ] Generates a structured test report documenting execution times, type validations, and edge-case null checks
- [ ] Allows dynamic adapter swapping without service restarts or container redeployments
- [ ] Replays queued DLQ events in batch and transitions their status to 'healed' with zero message loss
- [ ] Day 1: Implement FastAPI ingress gateway, Pydantic target schemas, and PostgreSQL DLQ tables.
- [ ] Day 2: Create DeepDiff structural drift extractor and seed 5 synthetic webhook mutation datasets (Stripe, GitHub, Shopify).
- [ ] Day 3: Build secure isolated Python execution runner with resource limits (timeout, no network, restricted builtins).
- [ ] Day 4: Implement LangGraph agent state machine with tool interfaces for schema retrieval and sandbox code execution.
- [ ] Day 5: Implement regression verification engine testing candidate functions against buffered valid payloads.
- [ ] Day 6: Build dynamic adapter hot-reloader and DLQ batch replay worker.
- [ ] Day 7: Develop Streamlit operator dashboard, run end-to-end evaluation benchmark suite, and document results.
- [ ] Unit tests for DeepDiff schema comparison logic and Pydantic validation error serialization
- [ ] Security tests for the execution sandbox verifying that socket, os.system, and open() operations raise security errors
- [ ] Integration tests running simulated webhook drift scenarios (e.g., customer_email -> user.contact.email) through the full LangGraph loop
- [ ] Adversarial prompt injection testing using malicious webhook payloads containing prompt override directives to verify prompt isolation
- [ ] Idempotency tests ensuring DLQ replay does not create duplicate database records or re-execute side effects
- [ ] Docker Compose stack orchestrating FastAPI gateway, PostgreSQL, Redis (job queue for agent triage), and Streamlit dashboard
- [ ] Local model execution support via Ollama (Llama-3-8B-Instruct) alongside cloud fallback options (Groq / OpenAI API)
- [ ] GitHub Actions CI pipeline executing automated linting (Ruff), security scanning (Bandit), and the full pytest regression suite

## Before completion

- [ ] Implement the planned MVP features.
- [ ] Add unit and integration tests.
- [ ] Run the test suite.
- [ ] Measure the evaluation metrics in the brief.
- [ ] Record actual results and known limitations.
- [ ] Document setup and deployment.
- [ ] Update the README to reflect the implemented features.
- [ ] Add only verified outcomes to your resume.
