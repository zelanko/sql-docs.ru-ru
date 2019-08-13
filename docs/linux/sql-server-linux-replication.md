---
title: Репликация SQL Server в Linux
description: В этой статье описана репликация SQL Server в Linux.
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
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68065196"
---
# <a name="sql-server-replication-on-linux"></a>Репликация SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В версии [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] реализована возможность репликации SQL Server для экземпляров SQL Server на Linux.

Для настройки репликации в Linux используйте [хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md) QL Server Management Studio (SSMS).

Экземпляр SQL Server может участвовать в любой роли репликации.

* Издатель
* Распространитель
* Подписчик

Схема репликации может сочетать и комбинировать платформы операционных систем. Например, схема репликации может включать экземпляр SQL Server на Linux для издателя и распространителя, а для подписчиков могут использоваться экземпляры SQL Server на Windows и Linux.

Экземпляры SQL Server на Linux могут участвовать в репликации любого типа.

* Транзакционная
* Объединить
* Моментальный снимок

Дополнительные сведения о репликации см. в разделе [Документация по репликации SQL Server](../relational-databases/replication/sql-server-replication.md).

## <a name="supported-features"></a>Поддерживаемые функции

Для [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] поддерживаются следующие функции репликации.

* репликация моментальных снимков;
* Репликация транзакций
* Репликация слиянием
* Одноранговая репликация
* Репликация с использованием портов, отличных от портов по умолчанию <!--Add link to explanation-->
* Репликация с проверкой подлинности AD
* Конфигурации репликации на базе Windows и Linux
* Немедленные обновления для репликации транзакций

## <a name="limitations"></a>Ограничения

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] не поддерживает следующие функции.

* Немедленное обновление для подписчиков
* публикация Oracle

## <a name="next-steps"></a>Следующие шаги

[Настройка репликации SQL Server в Linux](sql-server-linux-replication-tutorial-tsql.md)

[Пример: настройка репликации SQL Server в Linux](sql-server-linux-replication-configure.md)
