# Soru 1

* Müşteri adı, araç bilgileri ve ödemeye ait detayların olduğu tablo çekildi.
* Date kolonuna 3 saat eklendi ve array update edildi

```
SELECT
  name,
  c.id as car_ID,
  c.model as car_Model,
  m.year as manufacture_Year,
  ARRAY(select as struct p.* replace(timestamp_add(p.date, interval 3 hour) as date) 
  FROM unnest(purchase) as p) as purchase 
FROM dsmbootcamp.sample.semi_structured_hw
JOIN UNNEST(CAR) as c
JOIN UNNEST(MANUFACTURE) as m
ON c.id = m.id
```
