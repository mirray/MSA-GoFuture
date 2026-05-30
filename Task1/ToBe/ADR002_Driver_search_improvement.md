# ADR-002: Driver search improvement

**Status:** [Proposed | Accepted | Deprecated | Superseded by ADR-XXX]  
**Date:** YYYY-MM-DD  
**Author:** Marina Karmanova
**Stakeholders:** [List of affected teams/people]

---

## Executive Summary

We will use Redis cluster instead of elasticSearch for searching of drivers geoposition
---

## Context & Problem Statement

### Current State
Drivers for ride searches by geo-position stored in elasticsearch

### Business Requirements
*List what the business needs this solution to achieve.*
- **R4:** система обрабатывает более 200 тысяч конкурентных поездок без каскадных отказов - after 2 months
- **P1:** Обработка 500 тысяч конкурентных поездок - after 1 year
- **P2:** Горизонтальное масштабирование сразу в нескольких географических регионах

---

## Decision

Will use Redis cluster instead of elasticsearch, because it doesn't require read/write operations.
500000 simultaneous rides means more than 1500000 drivers, who send GPS data each 5-10 seconds (?).  -> 300000 RPS on write data
ElasticSearch cannot handle such amount of data. But Redis cluster can.
---

## Considered Alternatives

### Alternative 1: Keep elasticSearch

**Description:**  
Don't change anything, use elasticsearch cluster with spread by regions. 

**Pros:**
- No need to do anything

**Cons:**
- Will collapsed on high RPS


**Why rejected:**  
Not possible to handle required RPS

---

## Consequences

### Positive Outcomes ✅
- Fast in memory search for nearest drivers

### Negative Outcomes / Trade-offs ❌
- Don't store actual driver data
- If redis fall, lost driver data location (shouldn't be a problem, because GPS streaming data in real time, and we no need historical data of driver location)