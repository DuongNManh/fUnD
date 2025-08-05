# 🐘 PostgreSQL Performance Optimization Guide | Hướng dẫn Tối ưu Hiệu suất PostgreSQL

> **TOP 10 MOST CRITICAL configuration parameters for PostgreSQL performance optimization that you MUST know!**

---

## 1️⃣ `shared_buffers`

**English:**

- **Purpose:** Amount of RAM dedicated to caching data (tables & indexes)
- **Recommendation:** 25–40% of total RAM
- **Impact:** Improves read/write performance, reduces disk I/O

**Tiếng Việt:**

- **Mục đích:** Lượng RAM dùng để cache dữ liệu (bảng & chỉ mục)
- **Khuyến nghị:** 25–40% RAM tổng
- **Tác động:** Tăng tốc độ đọc/ghi, giảm truy cập đĩa vật lý

```sql
shared_buffers = 4GB  -- For 16GB RAM system
```

---

## 2️⃣ `work_mem`

**English:**

- **Purpose:** Max memory per query operation (sort, join, hash…)
- **Recommendation:** 4–64MB depending on connection count
- **Impact:** Too low slows queries; too high can exhaust RAM

**Tiếng Việt:**

- **Mục đích:** Bộ nhớ tối đa cho mỗi thao tác truy vấn (sort, join…)
- **Khuyến nghị:** 4–64MB tùy số kết nối
- **Tác động:** Thấp quá thì truy vấn chậm, cao quá thì dễ hết RAM

```sql
work_mem = 16MB
```

---

## 3️⃣ `maintenance_work_mem`

**English:**

- **Purpose:** Memory for maintenance tasks (VACUUM, CREATE INDEX…)
- **Recommendation:** 64–512MB
- **Impact:** Higher values speed up maintenance operations

**Tiếng Việt:**

- **Mục đích:** Bộ nhớ cho các thao tác bảo trì (VACUUM, tạo index…)
- **Khuyến nghị:** 64–512MB
- **Tác động:** Giá trị càng cao thì bảo trì càng nhanh

```sql
maintenance_work_mem = 256MB
```

---

## 4️⃣ `effective_cache_size`

**English:**

- **Purpose:** Hints PostgreSQL how much memory is available for caching (OS + DB)
- **Recommendation:** 50–75% total RAM
- **Impact:** Affects planner decisions between index vs sequential scan

**Tiếng Việt:**

- **Mục đích:** Gợi ý tổng lượng RAM hệ thống có thể dùng để cache (OS + PostgreSQL)
- **Khuyến nghị:** 50–75% RAM
- **Tác động:** Ảnh hưởng việc chọn seq scan hay index scan

```sql
effective_cache_size = 12GB
```

---

## 5️⃣ `max_connections`

**English:**

- **Purpose:** Maximum number of concurrent DB connections
- **Recommendation:** 100–200 (less if using PgBouncer)
- **Impact:** Too high wastes RAM; too low blocks clients

**Tiếng Việt:**

- **Mục đích:** Số kết nối tối đa vào DB
- **Khuyến nghị:** 100–200 (nếu có PgBouncer thì đặt thấp hơn)
- **Tác động:** Quá cao dễ cạn RAM, quá thấp dễ nghẽn kết nối

```sql
max_connections = 150
```

---

## 6️⃣ `wal_buffers`

**English:**

- **Purpose:** Memory for WAL (Write-Ahead Log) buffering
- **Recommendation:** 8–16MB (increase if heavy writes)
- **Impact:** Reduces write latency

**Tiếng Việt:**

- **Mục đích:** Bộ nhớ tạm cho WAL trước khi ghi ra đĩa
- **Khuyến nghị:** 8–16MB (tăng lên nếu workload ghi nhiều)
- **Tác động:** Giảm độ trễ ghi

```sql
wal_buffers = 16MB
```

---

## 7️⃣ `checkpoint_completion_target`

**English:**

- **Purpose:** Controls spread of checkpoint writes
- **Recommendation:** 0.7–0.9 (default = 0.5)
- **Impact:** Smooths I/O spikes during checkpoints

**Tiếng Việt:**

- **Mục đích:** Phân bố tốc độ ghi checkpoint để tránh đột biến I/O
- **Khuyến nghị:** 0.7–0.9 (mặc định 0.5)
- **Tác động:** Tránh “lag” trong các checkpoint

```sql
checkpoint_completion_target = 0.8
```

---

## 8️⃣ `max_wal_size` & `min_wal_size`

**English:**

- **Purpose:** Size thresholds for WAL segments
- **Recommendation:** `max_wal_size`: 1–4GB, `min_wal_size`: 80–256MB
- **Impact:** Controls checkpoint frequency and disk use

**Tiếng Việt:**

- **Mục đích:** Giới hạn kích thước WAL
- **Khuyến nghị:** `max_wal_size`: 1–4GB ; `min_wal_size`: 80–256MB
- **Tác động:** Ảnh hưởng tần suất checkpoint và dùng đĩa

```sql
max_wal_size = 2GB
min_wal_size = 128MB
```

---

## 9️⃣ `random_page_cost` & `seq_page_cost`

**English:**

- **Purpose:** Relative cost of random vs sequential disk reads
- **Recommendation:** SSD: random_page_cost = 1.1–2.0 ; HDD default = 4.0
- **Impact:** Influences planner to favor index or seq scans

**Tiếng Việt:**

- **Mục đích:** Đặt chi phí đọc ngẫu nhiên & tuần tự
- **Khuyến nghị:** SSD: random_page_cost = 1.1–2.0 ; seq_page_cost = 1.0
- **Tác động:** Ảnh hưởng lựa chọn index scan hay seq scan

```sql
seq_page_cost = 1.0
random_page_cost = 1.5
```

---

## 🔟 `autovacuum`

**English:**

- **Purpose:** Automatic cleanup of dead tuples to avoid table & index bloat
- **Recommendation:**

  - `autovacuum_vacuum_cost_limit`: 200–2000
  - `autovacuum_vacuum_scale_factor`: 0.1–0.2
  - `autovacuum_analyze_scale_factor`: 0.05–0.1

- **Impact:** Keeps database “clean” and performant over time

**Tiếng Việt:**

- **Mục đích:** Dọn dẹp tự động dead tuples, tránh phình bảng & index
- **Khuyến nghị:**

  - `autovacuum_vacuum_cost_limit`: 200–2000
  - `autovacuum_vacuum_scale_factor`: 0.1–0.2
  - `autovacuum_analyze_scale_factor`: 0.05–0.1

- **Tác động:** Duy trì hệ thống “sạch sẽ”, chạy lâu vẫn mượt!

```sql
autovacuum = on
autovacuum_vacuum_cost_limit = 1000
autovacuum_vacuum_scale_factor = 0.15
autovacuum_analyze_scale_factor = 0.075
```

---
