# JMeter performance test (shop.lab)

Test plan: `perf/jmeter/shop_loadtest.jmx`  
Results file: `perf/jmeter/results_4k_60s.jtl`  
HTML report: `perf/jmeter/reports/report_4k_60s/index.html`

## Run details
- Start: 2026-01-17 05:04
- End: 2026-01-17 05:07
- Target: https://shop.lab/
- Sampler: GET /

## Outcome (from JMeter HTML report)
- Total requests: 57,309
- Error rate: 6.55% (3,753 failures)
- Error type: SocketTimeoutException (Read timed out)
- Average latency: 4,035.38 ms
- Min / Max: 9 ms / 10,111 ms
- Throughput: 25.07 req/sec
- APDEX: 0.457 (T=500ms, F=1.5s)

## Notes
- 200 response is reachable, but timeouts appear under sustained load.
- Next step: tune timeouts, increase replicas, add HPA, and re-run.
