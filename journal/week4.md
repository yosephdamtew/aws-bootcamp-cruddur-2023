# Week 4 — Postgres and RDS
## I didn't configure the following command b/c I'm not sure if it would cost me or not.
```
aws rds create-db-instance \
  --db-instance-identifier cruddur-db-instance \
  --db-instance-class db.t3.micro \
  --engine postgres \
  --engine-version  14.6 \
  --master-username cruddurroot \
  --master-user-password zzpasswordzz \
  --allocated-storage 20 \
  --availability-zone us-east-1a \
  --backup-retention-period 0 \
  --port 5432 \
  --no-multi-az \
  --db-name cruddur \
  --storage-type gp2 \
  --publicly-accessible \
  --storage-encrypted \
  --enable-performance-insights \
  --performance-insights-retention-period 7 \
  --no-deletion-protection

  ....
  export PROD_CONNECTION_URL="postgresql://cruddurroot:@zzpasswordzz@zzzzz:5432/cruddur"
  gp env PROD_CONNECTION_URL="postgresql://cruddurroot:@zzpasswordzz@zzzzz:5432/cruddur"
```
