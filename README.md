## What you need to do
- Install docker and docker-compose
- clone this repository `git clone https://github.com/mahmoudSh58/prometheus_session.git`

## Lab 0: Prometheus on docker
```bash
docker volume create prometheus_data
docker run -d --name prometheus /
-p 9090:9090  /
-v prometheus_data:/prometheus /
-v $(pwd)/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus
```

### Lab 1: Prometheus and Alertmanager on docker
install DCGM exporter
```bash
export DCGM_EXPORTER_TAG=latest
docker run -d --rm \
    --name dcgm-exporter \
    --gpus all \
    --cap-add SYS_ADMIN \
    -p 9400:9400 \
    nvcr.io/nvidia/k8s/dcgm-exporter:${DCGM_EXPORTER_TAG}
```

```bash
docker compose up -d
```

