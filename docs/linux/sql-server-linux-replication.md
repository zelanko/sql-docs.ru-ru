---
title: Репликация SQL Server в Linux
description: В этой статье описана репликация SQL Server в Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 12/09/2019
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: f0e1acd5af76f5b0b075879fc1c5122713caed55
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75002045"
---
# <a name="sql-server-replication-on-linux"></a>Репликация SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В версии [!INCLUDE[SQL Server 2017](../includes/sssqlv14-md.md)] ([накопительный пакет обновления 18](https://support.microsoft.com/help/4527377)) и более поздних реализована возможность репликации SQL Server для экземпляров SQL Server на Linux.

Для настройки репликации в Linux используйте [хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md) QL Server Management Studio (SSMS).

Экземпляр SQL Server может участвовать в любой роли репликации.

* Издатель
* Распространитель
* Подписчик

Схема репликации может сочетать и комбинировать платформы операционных систем. Например, схема репликации может включать экземпляр SQL Server на Linux для издателя и распространителя, а для подписчиков могут использоваться экземпляры SQL Server на Windows и Linux.

Экземпляры SQL Server на Linux могут участвовать в репликации любого типа.

* Транзакционную
* Моментальный снимок

Дополнительные сведения о репликации см. в разделе [Документация по репликации SQL Server](../relational-databases/replication/sql-server-replication.md).

## <a name="supported-features"></a>Поддерживаемые функции

Поддерживаются следующие функции репликации:

* репликация моментальных снимков;
* Репликация транзакций
* Репликация с использованием портов, отличных от портов по умолчанию <!--Add link to explanation-->
* Репликация с проверкой подлинности AD
* Конфигурации репликации на базе Windows и Linux
* Немедленные обновления для репликации транзакций

## <a name="limitations"></a>Ограничения

Следующие возможности не поддерживаются:

* Репликация слиянием
* Одноранговая репликация
* публикация Oracle

## <a name="next-steps"></a>Дальнейшие действия

[Настройка репликации SQL Server в Linux](sql-server-linux-replication-tutorial-tsql.md)

[Пример: настройка репликации SQL Server в Linux](sql-server-linux-replication-configure.md)
