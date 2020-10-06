---
title: Поддерживаемые обновления версий и выпусков (SQL Server 2019)
description: Поддерживаемые обновления версий и выпусков SQL Server 2019.
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- components [SQL Server], adding to existing installations
- versions [SQL Server], upgrading
- upgrading SQL Server, upgrades supported
- cross-language support
ms.assetid: 702359c4-6ca9-42a8-860c-a95a802898a1
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions'
ms.openlocfilehash: 687f314e776dcc049f03cb4c8a164fb5fa84073e
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2020
ms.locfileid: "91670207"
---
# <a name="supported-version--edition-upgrades-sql-server-2019"></a>Поддерживаемые обновления версий и выпусков (SQL Server 2019)

[!INCLUDE [SQL Server -Windows Only](../../includes/applies-to-version/sql-windows-only.md)]
  
  Можно обновить версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], [!INCLUDE[sssql16-md](../../includes/sssql16-md.md)]и [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]. В этой статье приведены поддерживаемые пути обновления данных версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и поддерживаемые обновления выпусков [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)].  
  
## <a name="pre-upgrade-checklist"></a>Контрольный список действий перед обновлением  

- Перед началом обновления выпуска [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] до новой версии проверьте, поддерживаются ли используемые функции в версии, до которой производится обновление.  
- Проверьте наличие поддерживаемого [оборудования и программного обеспечения](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-ver15.md).
- Перед обновлением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]включите проверку подлинности Windows для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и проверьте необходимые настройки конфигурации по умолчанию: является ли учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] членом группы системных администраторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
- Для обновления до версии [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)]необходимо наличие поддерживаемой операционной системы. Дополнительные сведения см. в разделе [Требования к оборудованию и программному обеспечению для установки SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-ver15.md).  
- Обновление будет заблокировано, если компьютер ожидает перезагрузки.  
- Обновление будет заблокировано, если не запущена служба установщика Windows.

## <a name="unsupported-scenarios"></a>Неподдерживаемые сценарии

- Многоверсионные экземпляры в [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] не поддерживаются. Компоненты [!INCLUDE[ssDE](../../includes/ssde-md.md)] должны иметь один и тот же номер версии для одного экземпляра [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)].  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] доступен только для 64-разрядных платформ. Межплатформенное обновление не поддерживается. Невозможно обновить 32-разрядный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до стандартного 64-разрядного при помощи программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Но можно создать резервную копию или отсоединить базы данных от 32-разрядного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а затем восстановить их или присоединить к новому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (64-разрядная версия), если базы данных не опубликованы в репликации. Необходимо повторно создать имена входа и другие объекты пользователя в системных базах данных master, msdb и model.  
  
- Добавить новые компоненты в процессе обновления существующего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]нельзя. После обновления экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] добавить новые компоненты можно при помощи программы установки [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)]. Дополнительные сведения см. в разделе [Добавление компонентов в экземпляр SQL Server (программа установки)](./add-features-to-an-instance-of-sql-server-setup.md).  
 
## <a name="upgrades-from-earlier-versions-to-sssqlv15-md"></a>Обновление ранних версий до [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)]  
 
[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] поддерживает обновление со следующих версий SQL Server:

- [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 4 (SP4) или более поздней версии
- [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] с пакетом обновления 3 (SP3) или более поздней версии
- [!INCLUDE[ssSQL16](../../includes/sssql16-md.md)]с пакетом обновления 2 (SP2) или более поздней версии
- [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]

В таблице, представленной ниже, перечислены поддерживаемые сценарии обновления предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)].  
  
|Исходная версия|Поддерживаемые варианты обновления|  
|:------|:------|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Enterprise с пакетом обновления 4 (SP4)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Developer с пакетом обновления 4 (SP4)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/>[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Standard с пакетом обновления 4 (SP4)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Web с пакетом обновления 4 (SP4)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Express с пакетом обновления 4 (SP4) |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express <br/> <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Business Intelligence с пакетом обновления 4 (SP4)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Ознакомительная версия с пакетом обновления 4 (SP4)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Ознакомительная версия <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise с пакетом обновления 2 (SP2)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer с пакетом обновления 2 (SP2)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard с пакетом обновления 2 (SP2)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web с пакетом обновления 2 (SP2)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express с пакетом обновления 2 (SP2) |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence с пакетом обновления 2 (SP2)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Evaluation с пакетом обновления 2 (SP2)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Ознакомительная версия <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Enterprise|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Developer|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Standard|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Web|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Express |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5 Business Intelligence|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] 13.0.1601.5, ознакомительная версия|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Ознакомительная версия <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Enterprise|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Developer|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Standard|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Web|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Express |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Business Intelligence|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/> |  
|[!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] Ознакомительная версия|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Ознакомительная версия <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer|
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] версия-кандидат * |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise |  
|[!INCLUDE[sssqlv15_md](../../includes/sssqlv15-md.md)] Developer |[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise | 

 \* Предоставляемая корпорацией Майкрософт поддержка обновления с версий-кандидатов предназначена для клиентов, участвовавших в программе ранних последователей.

## <a name="migrate-to-sql-server-2019"></a>Миграция на SQL Server 2019

Вы можете выполнить миграцию баз данных из старых версий. Например, можно выполнить миграцию баз данных из [!INCLUDE [sskilimanjaro-md](../../includes/sskilimanjaro-md.md)] в SQL Server 2019.

Дополнительные сведения см. в [руководстве по миграции базы данных Azure](https://datamigration.microsoft.com/scenario/sql-to-sqlserver).

Следующие советы и средства помогут запланировать и реализовать миграцию.

- Средства миграции Миграцию поддерживает [помощник по миграции данных (DMA)](../../dma/dma-overview.md).
- Резервное копирование и восстановление Резервную копию, созданную в SQL Server 2008 или SQL Server 2008 R2, можно восстановить до SQL Server 2019.
- Доставка журналов Доставка журналов поддерживается, если основной экземпляр работает в SQL Server 2008 с пакетом обновления 3 (SP3) или более поздней версии либо в SQL Server 2008 R2 с пакетом обновления 2 (SP2) или более поздней версии, а дополнительный экземпляр — в SQL Server 2019. 

   > [!WARNING]
   > Если в результате автоматической или ручной отработки отказа экземпляр SQL Server 2019 станет основным, то экземпляр SQL Server 2008 или SQL Server 2008 R2 станет дополнительным и не сможет получать изменения от основного экземпляра.

- Массовая загрузка: Таблицы можно массово скопировать из SQL Server 2008 или SQL Server 2008 R2 в SQL Server 2019.

## <a name="sssqlv15-md-edition-upgrade"></a>[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Обновление выпуска 

В следующей таблице перечислены поддерживаемые сценарии обновлений в [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)].  

Пошаговые инструкции по обновлению выпуска см. в разделе [Обновление до другого выпуска SQL Server (программа установки)](../../database-engine/install-windows/upgrade-to-a-different-edition-of-sql-server-setup.md).  
  
|Исходная версия|Обновленная версия|  
|------------------|----------------|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (лицензия Server+CAL и Core) **|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise |  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Evaluation Enterprise **|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (лицензия Server+CAL или Core) <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> Обновление с переходом от Evaluation (бесплатного выпуска) на любой из платных выпусков поддерживается для изолированных, но не поддерживается для кластеризованных установок. Это ограничение не применяется к изолированным экземплярам, установленным в отказоустойчивом кластере Windows, входящем в группу доступности. |  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard **|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (лицензия Server+CAL или Core)|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer **|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (лицензия Server+CAL или Core) <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (лицензия Server+CAL или Core) <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Express *|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (лицензия Server+CAL или Core) <br/><br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard <br/> <br/> [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Web|  
  
 Кроме того, можно выполнить обновление выпуска между выпусками [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (лицензия Server+CAL) и [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (лицензия Core).  
  
|Обновление выпуска c|Обновление выпуска до|  
|--------------------------|------------------------|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (лицензия Server+CAL) **|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (лицензия Core)|  
|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (лицензия Core)|[!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise (лицензия Server+CAL)|  
  
 \* Также относится к [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] , экспресс-выпуск с инструментами и [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] , экспресс-выпуск с дополнительными службами.  
  
 ** Изменение выпуска кластеризованного экземпляра [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] ограничено. Следующие сценарии не поддерживаются для кластеров отработки отказа [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] .  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Enterprise до [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer, Standard или Evaluation.  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Developer до [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard или Evaluation.  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard до [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Evaluation.  
  
- [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Evaluation до [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)] Standard.  
  
## <a name="see-also"></a>См. также:  

 [Выпуски и поддерживаемые функции [!INCLUDE[sssqlv15-md](../../includes/sssqlv15-md.md)]](../../sql-server/editions-and-components-of-sql-server-version-15.md).

 [Требования к оборудованию и программному обеспечению для установки SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-ver15.md)

 [Обновление SQL Server](../../database-engine/install-windows/upgrade-sql-server.md)