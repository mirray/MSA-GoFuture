# ADR-001: Message Broker

**Status:** [Proposed | Accepted | Deprecated | Superseded by ADR-XXX]  
**Date:** YYYY-MM-DD  
**Author:** Marina Karmanova  
**Stakeholders:** [List of affected teams/people]

---

## Executive Summary

Компания использует RabbitMQ в качестве брокера сообщений, однако он не рассчитан на нагрузку в 500000 RPS мощности RabbitMQ будет не хватать для обработки всех сообщений.
Было принято решение переводить все новые микросервисы на Kafka и постепенно отказываться от RabbitMQ.
---

## Context & Problem Statement

### Current State
- Message Broker — RabbitMQ.
- Метрики очередей — RabbitMQ Exporter.
- Асинхронные вызовы — AMQP (RabbitMQ).

### Business Requirements
- **R4:** система обрабатывает более 200 тысяч конкурентных поездок без каскадных отказов - after 2 months
- **P1:** Обработка 500 тысяч конкурентных поездок - after 1 year

---

## Decision

Используем Kafka для всех новых микросервисов.

---

## Considered Alternatives

### Alternative 1: RabbitMQ + Kafka

**Description:**  
RabbitMQ Federation (on edge) with distributed nodes + Kafka for collecting global data from RabbitMQ

**Pros:**
- не нужно переводить на Кафку большинство функционала
- Distributed nodes могут в теории обрабатывать до 200k RPC на регион
- Хорошая масштабируемость

**Cons:**
- Сложная архитектура
- Все равно придется работать с Кафкой

**Why rejected:**  
Слишком сложно, при выходе например на Китай или Индию можем снова упереться в ограничения производительности
---

## Consequences

### Positive Outcomes ✅
- Увеличение производительности

### Negative Outcomes / Trade-offs ❌
- Requires some expertise

---

## References

- [Comparative Performance Evaluation of Apache Kafka and RabbitMQ in High-Throughput Distributed Systems](https://www.researchgate.net/publication/403962861_Comparative_Performance_Evaluation_of_Apache_Kafka_and_RabbitMQ_in_High-Throughput_Distributed_Systems)

---
