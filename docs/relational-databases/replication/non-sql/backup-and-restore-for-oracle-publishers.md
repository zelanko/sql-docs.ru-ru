---
title: Резервное копирование и восстановление для издателей Oracle | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server replication], Oracle publishing
- backups [SQL Server replication], Oracle publishing
- Oracle publishing [SQL Server replication], backup and restore
- restoring [SQL Server replication], Oracle publishing
ms.assetid: e5f181d0-cacf-442b-8b7a-202b3cfc358b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 21b2de27362455291c75e64c93ad6cf7e3529ca8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47833352"
---
# <a name="backup-and-restore-for-oracle-publishers"></a>Резервное копирование и восстановление для издателей Oracle
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  При резервном копировании и восстановлении соблюдайте следующие рекомендации:  
  
-   Убедитесь в том, что при резервном копировании издателя не запущен агент чтения журнала, а также в отсутствии любой активности в опубликованных таблицах баз данных.  
  
-   Производите резервное копирование издателя и распространителя одновременно.  
  
-   Если издатель или распространитель подлежат восстановлению, то повторно инициализируйте все подписки.  
  
-   Чтобы восстановить подписчика из резервной копии (без необходимости повторной инициализации подписки), должны быть сохранены транзакции, доставленные в базу данных подписки после последнего завершенного резервного копирования этой базы данных. Отрезок времени, в течение которого транзакции все еще доступны, зависит от установок хранения распространения. Сведения об этих настройках см. в статье [Окончание срока действия и отключение подписки](../../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
-   Если издатель или распространитель становятся несинхронизированными в результате восстановления базы данных, агент репликации производит в журнал записи об ошибке. В этом случае следует удалить и повторно создать все соответствующие публикации и подписки:  
  
    1.  Напишите скрипт определений публикаций и подписок. Дополнительные сведения см. в статье [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
         Если определение публикации изменило версию состояния издателя и распространителя, потребуется изменить скрипты.  
  
    2.  Удалите публикации и подписки.  
  
    3.  Выполните скрипты, созданные на шаге 1.  
  
     Если издатель должен быть удален и перенастроен заново, удалите открытый синоним **MSSQLSERVERDISTRIBUTOR** и пользователя настроенной репликации Oracle с помощью параметра **CASCADE** для удаления всех объектов репликации из издателя Oracle.  
  
## <a name="see-also"></a>См. также:  
 [Создание резервных копий реплицируемых баз данных и восстановление из них](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [Настройка издателя Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Обзор публикации Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  
