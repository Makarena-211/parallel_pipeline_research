# Иструкция по взаимодействию с виртуальными машинами 

### Создали 

```bash
limactl create --name pp-0 -y ~/pp-node.yaml
limactl create --name pp-1 -y ~/pp-node.yaml
```

### Запустили
```bash
limactl start pp-0
limactl start pp-1
```

### Проверили работоспособность и ресурсы
```bash
limactl list
limactl shell pp-0 -- nproc
limactl shell pp-1 -- nproc
limactl shell pp-0 -- free -h
limactl shell pp-1 -- free -h
limactl shell pp-1 -- df -h /
limactl shell pp-1 -- df -h /
```

### Проверили видят ли машины друг друга
```bash
limactl shell pp-0 -- ping -c 3 lima-pp-1.internal
limactl shell pp-1 -- ping -c 3 lima-pp-0.internal
```

### Остановили машины
```bash
parallel_pipeline_research % limactl stop pp-0
parallel_pipeline_research % limactl stop pp-1
```