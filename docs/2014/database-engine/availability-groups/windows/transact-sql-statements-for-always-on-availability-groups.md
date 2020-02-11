---
title: Общие сведения о инструкциях Transact-SQL для группы доступности AlwaysOn (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], Transact-SQL statements
ms.assetid: 184d0a81-2259-4db9-9d0d-01aac0b502c8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f635faa05d7d77a50d31491b1bab9b16875e728c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62813827"
---
# <a name="overview-of-transact-sql-statements-for-alwayson-availability-groups-sql-server"></a>Обзор сведений об инструкциях Transact-SQL для групп доступности AlwaysOn (SQL Server)
  В этом разделе приведены общие сведения об инструкциях [!INCLUDE[tsql](../../../includes/tsql-md.md)] , которые поддерживают развертывание [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , а также создание и управление данной группой доступности, репликой доступности и базой данных доступности.  
  
  
##  <a name="CreateEndpoint"></a>СОЗДАТЬ КОНЕЧНУЮ ТОЧКУ  
 [создать конечную точку... ДЛЯ DATABASE_MIRRORING](/sql/t-sql/statements/create-endpoint-transact-sql) создает конечную точку зеркального отображения базы данных, если она не существует на экземпляре сервера. Для каждого экземпляра сервера, на котором намечено развертывание [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] или зеркального отображения базы данных, требуется конечная точка зеркального отображения базы данных.  
  
 Эта инструкция выполняется на экземпляре сервера, на котором создается конечная точка. На каждом конкретном экземпляре сервера можно создать только одну конечную точку зеркального отображения базы данных. Дополнительные сведения см. в разделе [Конечная точка зеркального отображения базы данных (SQL Server)](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md).  
  
##  <a name="CreateAG"></a>СОЗДАНИЕ ГРУППЫ ДОСТУПНОСТИ  
 [Создать группу доступности](/sql/t-sql/statements/create-availability-group-transact-sql) создает новую группу доступности и при необходимости прослушиватель группы доступности. Как минимум необходимо указать экземпляр локального сервера, который станет начальной первичной репликой. Дополнительно можно указать до четырех вторичных реплик.  
  
 Выполните CREATE AVAILABILITY GROUP в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], на котором должна размещаться начальная первичная реплика создаваемой группы доступности. Этот экземпляр сервера должен находиться на узле отказоустойчивого кластера Windows Server (WSFC) (Дополнительные сведения см. в разделе [Предварительные требования, ограничения и рекомендации для группы доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
##  <a name="AlterAG"></a>ALTER AVAILABILITY GROUP  
 [Инструкция ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) поддерживает изменение существующей группы доступности или прослушивателя группы доступности, а также отработку отказа группы доступности.  
  
 Выполните ALTER AVAILABILITY GROUP в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором размещается текущая первичная реплика.  
  
##  <a name="AlterDb"></a>ИЗМЕНИТЬ БАЗУ ДАННЫХ... ЗАДАТЬ HADR...  
 Параметры предложения [SET HADR](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) инструкции ALTER DATABASE позволяют присоединить базу данных-получателя к группе доступности соответствующей базы данных-источника, удалить присоединенную базу данных, отложить синхронизацию данных в присоединенной базе данных, а также возобновить синхронизацию данных.  
  
##  <a name="DropAG"></a>УДАЛИТЬ ГРУППУ ДОСТУПНОСТИ  
 [Удалить группу доступности](/sql/t-sql/statements/drop-availability-group-transact-sql) удаляет указанную группу доступности и все ее реплики. Инструкция DROP AVAILABILITY GROUP может быть запущена с любого узла [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в отказоустойчивом кластере WSFC.  
  
##  <a name="Restrictions"></a>Ограничения для инструкций группы доступности Transact-SQL  
 Инструкции CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP и DROP AVAILABILITY GROUP [!INCLUDE[tsql](../../../includes/tsql-md.md)] имеют следующие ограничения.  
  
-   За исключением DROP AVAILABILITY GROUP, для выполнения этих инструкций требуется, чтобы была включена служба HADR на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Включение и отключение групп доступности AlwaysOn (SQL Server)](enable-and-disable-always-on-availability-groups-sql-server.md).  
  
-   Эти инструкции не могут выполняться в пределах транзакций или пакетов.  
  
-   Несмотря на то, что эти инструкции предназначены для восстановления после сбоя, они не гарантируют выполнения отката всех изменений при сбое. Однако системы должны быть способны четко выполнять обработку и пропуск частичных сбоев.  
  
-   Эти инструкции не поддерживают выражения или переменные.  
  
-   Если во время действия группы доступности или восстановления выполняется инструкция [!INCLUDE[tsql](../../../includes/tsql-md.md)] , эта инструкция возвращает ошибку. В случае необходимости дождитесь завершения действия или восстановления, а затем повторно выполните инструкцию.  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
