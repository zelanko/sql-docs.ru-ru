# [Сведения о SQL Server на Linux](sql-server-linux-overview.md)

# Обзор
## [Заметки о выпуске](sql-server-linux-release-notes.md)
## [Новые возможности в этом выпуске](sql-server-linux-whats-new.md)
## [Новые и обновленные Статьи](new-updated-linux.md)
## [Выпуски и поддерживаемые функции](sql-server-linux-editions-and-components-2017.md)

# Краткие руководства
## [Установка и подключение — Red Hat](quickstart-install-connect-red-hat.md)
## [Установка и подключение — SUSE](quickstart-install-connect-suse.md)
## [Установка и подключение — Ubuntu](quickstart-install-connect-ubuntu.md)
## [Запуск и подключение — Docker](quickstart-install-connect-docker.md)
## [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)
## [Запуск и подключение — облако](quickstart-install-connect-clouds.md)

# Учебники
## [1_Миграция с Windows](sql-server-linux-migrate-restore-database.md)
## [2_Миграция с Oracle](../ssma/oracle/sql-server-linux-convert-from-oracle.md?toc=%2fsql%2flinux%2ftoc.json)
## [3_Миграция в Docker](tutorial-restore-backup-in-sql-server-container.md)
## [4_Создание задания](sql-server-linux-run-sql-server-agent-job.md)
## [5_Настройка проверки подлинности AD](sql-server-linux-active-directory-authentication.md)
## [6_Создание экземпляра отказоустойчивого кластера](sql-server-linux-shared-disk-cluster-configure.md)
### [iSCSI](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
### [NFS](sql-server-linux-shared-disk-cluster-configure-nfs.md)
### [SMB](sql-server-linux-shared-disk-cluster-configure-smb.md)
## [7_Развертывание кластера Pacemaker](sql-server-linux-deploy-pacemaker-cluster.md)
## [8_Создание и настройка групп доступности](sql-server-linux-create-availability-group.md)
## [9_Настройка Kubernetes для высокого уровня доступности](tutorial-sql-server-containers-kubernetes.md)

# Основные понятия
## Установить
### [Установка SQL Server](sql-server-linux-setup.md)
### [Установка средств SQL Server](sql-server-linux-setup-tools.md)
### [Установка агента SQL Server](sql-server-linux-setup-sql-agent.md)
### [Установка полнотекстового поиска SQL Server](sql-server-linux-setup-full-text-search.md)
### [Установка служб SQL Server Integration Services](sql-server-linux-setup-ssis.md)
### [Настройка репозиториев](sql-server-linux-change-repo.md)

## Configure
### [Настройка с помощью mssql-conf](sql-server-linux-configure-mssql-conf.md)
### [Переменные сред](sql-server-linux-configure-environment-variables.md)
### [Настройка контейнеров Docker](sql-server-linux-configure-docker.md)
### [Отзывы пользователей](sql-server-linux-customer-feedback.md)

## [Разработка](sql-server-linux-develop-overview.md)
### [Библиотеки подключений](sql-server-linux-develop-connectivity-libraries.md)
### [Использование Visual Studio Code](sql-server-linux-develop-use-vscode.md)
### [Использование SSMS](sql-server-linux-develop-use-ssms.md)
### [Использование SSDT](sql-server-linux-develop-use-ssdt.md)

## [Управление](sql-server-linux-management-overview.md)
### [Использование для управления SSMS](sql-server-linux-manage-ssms.md)
### [Использование для управления PowerShell](sql-server-linux-manage-powershell.md)
### [Использование доставки журналов](sql-server-linux-use-log-shipping.md)
### [Использование DB Mail и оповещений по почте](sql-server-linux-db-mail-sql-agent.md)
### [Настройка нескольких подсетей для доступности](sql-server-linux-configure-multiple-subnet.md)

## [анализа](sql-server-linux-migrate-overview.md)
### [Экспорт и импорт BACPAC из Windows](sql-server-linux-migrate-ssms.md)
### [Миграция с помощью помощника по миграции SQL Server (SSMA)](sql-server-linux-migrate-ssma.md)
### [Массовое копирование с помощью bcp](sql-server-linux-migrate-bcp.md)

## [Извлечение, преобразование и загрузка](sql-server-linux-migrate-ssis.md)
### [Ограничения и известные проблемы](sql-server-linux-ssis-known-issues.md)
### [Настройка служб SSIS](sql-server-linux-configure-ssis.md)
### [Планирование пакетов служб SSIS](sql-server-linux-schedule-ssis-packages.md)

## [Настройка непрерывности бизнес-процессов](sql-server-linux-business-continuity-dr.md)
### [Основы доступности](sql-server-linux-ha-basics.md)
### [Архивация и восстановление](sql-server-linux-backup-and-restore-database.md)
#### [Интерфейс виртуальных устройств — Linux](sql-server-linux-backup-vdi-specification.md)
### [Экземпляр отказоустойчивого кластера](sql-server-linux-shared-disk-cluster-concepts.md)
#### [Red Hat Enterprise Linux (RHEL)]()
##### [Настройка (дополнение HA)](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)
##### [Работа (дополнение HA)](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
#### [SUSE Linux Enterprise Server (SLES)]()
##### [Настройка (дополнение HA)](sql-server-linux-shared-disk-cluster-sles-configure.md)
### [Группы доступности](sql-server-linux-availability-group-overview.md)
#### [Обеспечение высокой доступности](sql-server-linux-availability-group-ha.md)
##### [Настройка группы доступности](sql-server-linux-availability-group-configure-ha.md)
##### [Настройка в RHEL](sql-server-linux-availability-group-cluster-rhel.md)
##### [Настройка на SLES](sql-server-linux-availability-group-cluster-sles.md)
##### [Настройка в Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)
##### [Эксплуатация](sql-server-linux-availability-group-failover-ha.md)
#### [Создание только для чтения и масштабирования]()
##### [Настройка группы доступности](sql-server-linux-availability-group-configure-rs.md)
#### [Настройка кроссплатформенности (Windows и Linux)](sql-server-linux-availability-group-cross-platform.md)

## [безопасность](sql-server-linux-security-overview.md)
### [Начало работы с функциями безопасности](sql-server-linux-security-get-started.md)
### [Шифрование подключений](sql-server-linux-encrypted-connections.md)

## Производительность
### [Рекомендации](sql-server-linux-performance-best-practices.md)
### [Начало работы с функциями повышения производительности](sql-server-linux-performance-get-started.md)

# Примеры
## Автоматическая установка
### [Red Hat Enterprise Linux (RHEL)](sample-unattended-install-redhat.md)
### [SUSE Linux Enterprise Server (SLES)](sample-unattended-install-suse.md)
### [Ubuntu](sample-unattended-install-ubuntu.md)

# Ресурсы
## [Вопросы и ответы](sql-server-linux-faq.md)
## [Диагностика](sql-server-linux-troubleshooting-guide.md)
## [Документация по SQL Server](../sql-server/sql-server-technical-documentation.md)
## Участники
### [Мониторинг](../sql-server/partner-monitor-sql-server.md)
### [Высокий уровень доступности и аварийное восстановление](../sql-server/partner-hadr-sql-server.md)
### [Управление](../sql-server/partner-management-sql-server.md)
### [Разработка](../sql-server/partner-dev-sql-server.md)
## [Stack Exchange DBA](https://dba.stackexchange.com/questions/tagged/sql-server)
## [Stack Overflow](http://stackoverflow.com/questions/tagged/sql-server)
## [Форумы MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
## [Отправить отзыв.](https://feedback.azure.com/forums/908035-sql-server)
## [Reddit](https://www.reddit.com/r/SQLServer)
