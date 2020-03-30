---
title: Заметки о выпуске SQL Server 2019 | Документация Майкрософт
description: Узнайте об ограничениях SQL Server 2019 (15.x), известных проблемах, справочных ресурсах и других заметках о выпуске.
ms.date: 11/04/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 0d27209448ece622a4906f6ba2cae28268c0210a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "79190600"
---
# <a name="sql-server-2019-release-notes"></a>Заметки о выпуске [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В статье описаны ограничения и известные проблемы, связанные с [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]. Связанные сведения:

> [Новые возможности версии [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]](../sql-server/what-s-new-in-sql-server-ver15.md)

## [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] — это последний общедоступный выпуск [!INCLUDE[SQL Server 2019](../includes/ssnoversion-md.md)].

Полные сведения о лицензировании доступны в папке `License Terms` на установочном носителе.

## <a name="documentation"></a>Документация

- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] может быть отфильтрована по версии. Используйте элемент управления в верхней левой части каждой страницы документации для фильтрации в соответствии с вашими требованиями.

## <a name="build-number"></a>Номер сборки

Номер RTM-сборки для SQL Server 2019 — `15.0.2000.5`.

[!INCLUDE [sql-server-servicing-updates-version-15](../includes/sql-server-servicing-updates-version-15.md)]

## <a name="sql-server-installation-may-fail-if-ssms-18x-is-installed"></a>Установка SQL Server может быть прервана, если установлена среда SSMS 18.x.

- **Проблема и последствия для клиентов**: при установке [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] происходит сбой, если следующие установки выполняются в приведенном ниже порядке:
  1. SQL Server Management Studio (SSMS) версии 18.0, 18.1, 18.2 или 18.3 установлена на сервере.
  1. Предпринята попытка установки [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] со съемного носителя. Например, с установочного носителя DVD.

- **Возможное решение**:
  1. Удалите любую версию SSMS выше, чем SSMS 18.3.1.
  1. Установите более новую версию SSMS (18.3.1 или новее). Для получения последней версии обратитесь к статье [Скачивание SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md).
  1. Установите [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] как обычно.

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]

## <a name="utf-8-collations"></a>Параметры сортировки UTF-8

- **Проблема и последствия для клиентов**: Параметры сортировки с поддержкой UTF-8 невозможно использовать со следующими компонентами:
  - [Таблицы выполняющихся в памяти OLTP](../relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables.md)
  - [Always Encrypted с безопасными анклавами](../relational-databases/security/encryption/always-encrypted-enclaves.md) (если не используются безопасные анклавы, [Always Encrypted](../relational-databases/security/encryption/always-encrypted-database-engine.md) может использовать UTF-8)

  > [!WARNING]
  > Создание файла [BACPAC](../relational-databases/data-tier-applications/data-tier-applications.md#bacpac) базы данных со столбцами таблицы, определяемыми как [CHAR или VARCHAR](../t-sql/data-types/char-and-varchar-transact-sql.md), размером более 4000 байтов, завершится сбоем.
  
  > [!NOTE]
  > В настоящее время в пользовательском интерфейсе нет возможности выбрать параметры сортировки с поддержкой UTF-8 в Azure Data Studio или SQL Server Data Tools (SSDT). Последняя версия [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (SSMS) 18 поддерживает выбор параметров сортировки UTF-8 в пользовательском интерфейсе.

- **Область применения**: RTM-версия [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]

## <a name="master-data-service-notification-email-contains-broken-link"></a>Уведомление от службы Master Data Services по электронной почте содержит неработающую ссылку

- **Проблема и последствия для клиентов**: Сообщение электронной почты с уведомлением от службы Master Data Services (MDS) содержит неработающую ссылку. Ссылка ведет на страницу, которая возвращает сообщение об ошибке наподобие следующего:

   `The view 'Index' or its master was not found or no view engine supports the searched locations.`

- **Возможное решение**: Откройте портал MDS и перейдите к ресурсу вручную.

- **Область применения**: RTM-версия [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]

## <a name="see-also"></a>См. также раздел

- [Требования к оборудованию и программному обеспечению для установки SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-ver15.md)

## <a name="machine-learning-services"></a>Служба машинного обучения

Сведения о проблемах в Службах машинного обучения SQL Server см. в статье [Known issues in SQL Server Machine Learning Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md) (Известные проблемы в Службах машинного обучения SQL Server).

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]
