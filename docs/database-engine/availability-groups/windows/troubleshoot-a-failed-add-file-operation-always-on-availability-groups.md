---
title: Сбой операции добавления файла для группы доступности
decription: Possible resolutions for failing to add a file to an availability group.
ms.custom: seo-lt-2019
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary databases [SQL Server], Availability Groups
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 31ceaebf-864b-4dd0-9112-0d047b0316ad
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1655992526096035eb109821d8950980921951ad
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75251219"
---
# <a name="troubleshoot-a-failed-add-file-operation-always-on-availability-groups"></a>Устранение неполадок с операцией добавления файла, завершившейся сбоем (группы доступности AlwaysOn)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В некоторых развертываниях групп доступности AlwaysOn различаются пути в системах, где размещены первичная и вторичная реплики. Если путь к файлу операции добавления файла во вторичной реплике не существует, то будет выполнена успешно операция добавления файлов в базе данных-источнике. Однако операция добавления файла приводит к приостановке базы данных-получателя. Это, в свою очередь, вызовет переход дополнительной реплики в состояние NOT SYNCHRONIZING.  
  
> [!NOTE]  
>  Рекомендуется, чтобы при возможности путь к файлам (в том числе буква диска) базы данных-получателя совпадала с путем соответствующей базы данных-источника.  
  
## <a name="problem-resolution"></a>Решение проблем  
 Чтобы разрешить эту проблему, владелец базы данных должен выполнить следующие шаги.  
  
1.  Удалите базу данных-получатель из группы доступности. Дополнительные сведения см. в разделе [Удаление базы данных-получателя из группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/remove-a-secondary-database-from-an-availability-group-sql-server.md).  
  
2.  В существующей базе данных-получателе выполните восстановление полной резервной копии файловой группы, содержащей файл, добавленный в базу данных-получатель, применив параметры WITH NORECOVERY и WITH MOVE (задав путь файла на экземпляре сервера, на котором размещена дополнительная реплика). Дополнительные сведения см. в разделе [Восстановление базы данных в новое расположение (SQL Server)](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md).  
  
3.  Создайте резервную копию журнала транзакций, содержащего операцию добавления файла, в базе данных-источнике и вручную восстановите эту резервную копию журналов в базе данных-получателе с помощью параметров WITH NORECOVERY и WITH MOVE.  
  
4.  Подготовьте базу данных-получатель к повторному присоединению к группе доступности, выполнив восстановление с параметром NO RECOVERY остальных ожидающих резервных копий журналов из базы данных-источника.  
  
5.  Повторно присоедините базу данных-получатель к группе доступности. Дополнительные сведения см. в статье [Присоединение базы данных-получателя к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Подготовка базы данных-получателя для присоединения к группе доступности вручную (SQL Server)](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)   
 [Диагностика пользователей, утративших связь с учетной записью (SQL Server)](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)   
 [Поиск и устранение неисправностей конфигурации групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)
