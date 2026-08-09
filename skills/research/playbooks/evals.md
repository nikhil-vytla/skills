### Evals

**Use when:** the task is building a new eval or running an existing one to answer a question about model quality.

> Stub — flesh out with the actual steps you follow once this has been used a few times. Placeholder shape below.

1. Pin down what the eval is meant to distinguish — which two outcomes must produce different scores — before building it.
2. Check for an existing eval that already answers this before building a new one.
3. Build the smallest eval that captures the distinction, with a known-correct case to sanity-check scoring.
4. Run it, sanity-check a sample of individual scores by hand before trusting the aggregate.
5. Report the result with the eval's limitations stated alongside the number.
