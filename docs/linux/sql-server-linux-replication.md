---
title: Репликация SQL Server в Linux
description: В этой статье описывается репликация SQL Server в Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 10/17/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b049866d9752485cb1b9eb609404a3bd86f28a41
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065196"
---
# <a name="sql-server-replication-on-linux"></a>Репликация SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] Представляет репликации SQL Server для экземпляров SQL Server в Linux.

Настройка репликации на платформе Linux с помощью SQL Server Management Studio (SSMS) [хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

Экземпляр SQL Server может участвовать в любую роль репликации:

* Издатель
* Распространитель
* Подписчик

Схема репликации можно комбинировать и сопоставлять платформ операционных систем. Например схема репликации может включать экземпляра SQL Server в Linux для издателя и распространителя и подписчиков включают экземпляров SQL Server на Windows, а также для Linux.

Экземпляры SQL Server в Linux может участвовать в любой тип репликации.

* Транзакционная
* Объединить
* Моментальный снимок

Подробные сведения о репликации см. в разделе [руководство по репликации SQL Server](../relational-databases/replication/sql-server-replication.md).

## <a name="supported-features"></a>Поддерживаемые функции

Для [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] поддерживаются следующие функции репликации:

* репликация моментальных снимков;
* Репликация транзакций
* Репликация слиянием
* Peer-to-Peer репликации
* Репликация с помощью порты не по умолчанию <!--Add link to explanation-->
* Репликация с использованием проверки подлинности AD
* Конфигурации репликации между Windows и Linux
* Сразу же видеть обновление для репликации транзакций

## <a name="limitations"></a>Ограничения

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] не поддерживает следующие функции:

* Немедленное обновление подписчиков
* публикация Oracle

## <a name="next-steps"></a>Следующие шаги

[Настройка репликации SQL Server в Linux](sql-server-linux-replication-tutorial-tsql.md)

[Пример: Настройка репликации SQL Server в Linux](sql-server-linux-replication-configure.md)
