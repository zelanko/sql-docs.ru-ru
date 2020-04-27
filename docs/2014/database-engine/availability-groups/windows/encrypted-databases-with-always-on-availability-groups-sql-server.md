---
title: Зашифрованные базы данных с группы доступности AlwaysOn (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption, AlwaysOn Availability Groups
- TDE, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 09eb6ebc-3051-4fff-86a5-93524507b1fc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5bafd990a7c115a6108b699a61897f9e587e83c4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62814640"
---
# <a name="encrypted-databases-with-alwayson-availability-groups-sql-server"></a>Зашифрованные базы данных с группами доступности AlwaysOn (SQL Server)
  В этом разделе приведены сведения об использовании зашифрованных или недавно расшифрованных баз данных с использованием [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **В этом разделе.**  
  
-   [Ограничения](#Restrictions)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Если база данных зашифрована или содержит ключ шифрования базы данных, то нельзя использовать [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] или [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] для добавления базы данных в группу доступности. Если зашифрованная база данных была расшифрована, то в резервных копиях ее журналов могут содержаться зашифрованные данные. В этом случае выполнение полной начальной синхронизации данных в базе данных может завершиться ошибкой. Причина этого заключается в том, что операции восстановления журнала может потребоваться сертификат, который был использован ключами шифрования базы данных, который в данный момент недоступен.  
  
     Чтобы сделать расшифрованную базу данных доступной для добавления в группу доступности с помощью мастера, выполните следующие шаги.  
  
    1.  Создайте резервную копию журнала базы данных-источника.  
  
    2.  Создайте полную резервную копию базы данных-источника.  
  
    3.  Восстановите резервную копию базы данных на экземпляре сервера, на котором размещается вторичная реплика.  
  
    4.  Создайте новую резервную копию журнала базы данных-источника.  
  
    5.  Восстановите эту резервную копию журнала в базе данных-получателе.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
  
-   [Подготовка базы данных-получателя для присоединения к группе доступности вручную (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Использование мастера групп доступности (среда SQL Server Management Studio)](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Использование мастера добавления базы данных в группу доступности (среда SQL Server Management Studio)](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Прозрачное шифрование данных (TDE)](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
  
