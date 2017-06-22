---
title: "Издатели, отличные от издателей SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- heterogeneous database replication, non-SQL Server Publishers
- non-SQL Server Publishers
- heterogeneous data sources, non-SQL Server Publishers
- Publishers [SQL Server replication], Oracle
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 72a1a8c69a7c18f02da6439af94fefffe73a03a3
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="non-sql-server-publishers"></a>издатели, отличные от издателей SQL Server
  Публикация данных из источников, отличных от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , позволяет консолидировать данные в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может использовать подписку на моментальные снимки или транзакционные данные, публикуемые из базы данных Oracle. Дополнительные сведения о публикациях из Oracle см. в статье [Обзор публикации Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
 Разнородная репликация на подписчики, отличные от подписчика SQL Server, устарела. Публикация Oracle устарела. Для перемещения данных создайте решения с помощью системы отслеживания измененных данных и служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Публикация из баз данных, отличных от баз данных[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , прекрасно подходит для следующих сценариев:  
  
|Сценарий|Описание|  
|--------------|-----------------|  
|Развертывание приложений на платформе[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework|Разработка при помощи [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при работе с данными, реплицируемыми из базы данных, отличающейся от базы данных[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Серверы промежуточного хранения данных|Поддержание синхронизации промежуточных баз данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с базой данных, отличной от базы данных[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Переход на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Протестируйте приложения в реальном времени совместно с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при репликации изменений исходной системы. Переключение на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при успешном испытании миграции.|  
  
## <a name="see-also"></a>См. также:  
 [Heterogeneous Database Replication](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)  
  
  
