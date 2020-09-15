---
title: Модель восстановления базы данных
description: Узнайте, как включить политику для проверки модели восстановления резервной копии для пользовательских баз данных, чтобы снизить потери данных.
ms.custom: seo-lt-2019
ms.date: 08/31/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 048fa8d28e32ad73aa9e2a85e217f268fa865a3c
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/01/2020
ms.locfileid: "89285255"
---
# <a name="database-recovery-model"></a>Модель восстановления базы данных
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В выпусках SQL Server Enterprise и Standard это правило проверяет наличие пользовательских баз данных с возможностью записи и простой моделью восстановления. Для производственных баз данных рекомендуется использовать модель полного восстановления вместо простой. Режим полного восстановления делает возможным восстановление данных на момент времени. Это позволяет снизить потери данных при аварийном восстановлении.
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Чтобы обеспечить возможность восстановления с минимальной потерей данных, для производственных баз данных следует применять режим полного восстановления и запланировать частое создание резервных копий журнала транзакций.
  
## <a name="see-also"></a>См. также раздел 
  
 [Обзор процессов восстановления](../backup-restore/restore-and-recovery-overview-sql-server.md)   
  
 [Выполнение полного восстановления базы данных (модель полного восстановления)](../backup-restore/complete-database-restores-full-recovery-model.md)  

 [Резервные копии журналов транзакций](../backup-restore/transaction-log-backups-sql-server.md)   
  
