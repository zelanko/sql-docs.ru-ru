---
title: Устранение неполадок при выполнении операции добавления файла (группы доступности AlwaysOn) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary databases [SQL Server], Availability Groups
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 31ceaebf-864b-4dd0-9112-0d047b0316ad
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6940e9e40a09e5bd0c7afc591b34c17129350d74
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62813444"
---
# <a name="troubleshoot-a-failed-add-file-operation-alwayson-availability-groups"></a>Устранение неполадок с операцией добавления файла, давшей сбой (группы доступности AlwaysOn)
  В некоторых развертываниях групп доступности AlwaysOn различаются пути в системах, где размещена первичная реплика и где размещена вторичная реплика. Если путь к файлу операции добавления файла во вторичной реплике не существует, то будет выполнена успешно операция добавления файлов в базе данных-источнике. Однако операция добавления файла приводит к приостановке базы данных-получателя. Это, в свою очередь, вызовет переход дополнительной реплики в состояние NOT SYNCHRONIZING.  
  
> [!NOTE]  
>  Рекомендуется, чтобы при возможности путь к файлам (в том числе буква диска) базы данных-получателя совпадала с путем соответствующей базы данных-источника.  
  
## <a name="problem-resolution"></a>Решение проблем  
 Чтобы разрешить эту проблему, владелец базы данных должен выполнить следующие шаги.  
  
1.  Удалите базу данных-получатель из группы доступности. Дополнительные сведения см. в разделе [Удаление базы данных-получателя из группы доступности (SQL Server)](remove-a-secondary-database-from-an-availability-group-sql-server.md).  
  
2.  В существующей базе данных-получателе выполните восстановление полной резервной копии файловой группы, содержащей файл, добавленный в базу данных-получатель, применив параметры WITH NORECOVERY и WITH MOVE (задав путь файла на экземпляре сервера, на котором размещена дополнительная реплика). Дополнительные сведения см. в разделе [Восстановление базы данных в новое расположение (SQL Server)](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md).  
  
3.  Создайте резервную копию журнала транзакций, содержащего операцию добавления файла, в базе данных-источнике и вручную восстановите эту резервную копию журналов в базе данных-получателе с помощью параметров WITH NORECOVERY и WITH MOVE.  
  
4.  Подготовьте базу данных-получатель к повторному присоединению к группе доступности, выполнив восстановление с параметром NO RECOVERY остальных ожидающих резервных копий журналов из базы данных-источника.  
  
5.  Повторно присоедините базу данных-получатель к группе доступности. Дополнительные сведения см. в статье [Присоединение базы данных-получателя к группе доступности (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Подготовка базы данных-получателя для присоединения к группе доступности вручную (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)   
 [Диагностика пользователей, утративших связь с учетной записью (SQL Server)](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)   
 [Устранение неполадок &#40;конфигурации группы доступности AlwaysOn SQL Server&#41;Deleted](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
