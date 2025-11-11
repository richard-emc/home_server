# Tasks.md – Tarefas Agendadas no Home Server (OMV + Docker)

Este arquivo centraliza **todas as tarefas agendadas** no OpenMediaVault (via *Scheduled Tasks*), incluindo:
- As que **já estão rodando** (baseadas no seu setup atual).
- **Novas tarefas sugeridas** (fáceis de implementar, sem custo).
- Status, frequência, script associado e integração com o GitHub.

| # | Tarefa | Frequência | Script / Comando | Descrição | Status |
|---|--------|------------|------------------|-----------|--------|
| 1 | **Backup de Configs Docker** | Diário (02:00) | `bash /scripts/backup_docker_configs.sh` | Copia pastas `/Compose/*/config/` → `/Backup/docker_configs/` com data | Ativo |
| 2 | **Limpeza de Logs Antigos** | Semanal (Domingo 03:00) | `find /var/log -type f -mtime +30 -delete` | Remove logs com mais de 30 dias | Ativo |
| 3 | **Verificação de Integridade RAID1** | Mensal (1º dia, 04:00) | `cat /proc/mdstat && mdadm --detail /dev/md0` | Loga status do RAID no `/scripts/logs/raid_check.log` | Ativo |
| 4 | **Atualização de Imagens Docker** | Semanal (Sábado 05:00) | `bash /scripts/update_docker_images.sh` | `docker-compose pull` em todos os stacks | Ativo |
| 5 | **Restart de Serviços Críticos (se falhar)** | Diário (06:00) | `bash /scripts/health_check_restart.sh` | Checa Jellyfin, Immich, HA → restart se down | Ativo |
| 6 | **Backup para Nuvem (Rclone + Google Drive)** | Diário (01:30) | `backup_to_gdrive.sh` | Sync `/Backup/` → Google Drive (15GB grátis) | Alta |
| 7 | **Relatório de Uso de Disco** | Diário (07:00) | `disk_usage_report.sh` | `df -h` + `du` dos volumes → envia por email | Alta |
| 8 | **Limpeza Automática de Downloads Antigos** | Diário (00:30) | `clean_downloads.sh` | Deleta arquivos em `/Media/media_server/downloads/` com >7 dias | Média |
| 9 | **Monitoramento de CPU/RAM com Alerta** | A cada 6h | `resource_monitor.py` | Usa `psutil` → envia email se CPU >90% por 5min | Média |
| 10 | **Verificação de Atualizações do Sistema** | Semanal (Segunda 08:00) | `check_system_updates.sh` | `apt update && apt list --upgradable` → log | Baixa |
| 11 | **Teste Automático de Restore (Backup)** | Mensal (15º dia, 03:30) | `test_restore.sh` | Restaura um arquivo aleatório de backup → valida integridade | Alta |
| 12 | **Sync de Fotos com Dispositivo Móvel** | Diário (23:00) | `mobile_photo_sync.sh` | Usa `rclone` ou `syncthing` para puxar do celular | Média |
| 13 | **Geração de Relatório Semanal (Markdown)** | Semanal (Domingo 08:00) | `weekly_report.sh` | Gera `reports/YYYY-MM-DD.md` com: uptime, backups, uso de disco | Baixa |