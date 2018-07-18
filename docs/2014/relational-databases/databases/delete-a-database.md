---
title: Удаление базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database removal [SQL Server], SQL Server Management Studio
- removing databases
- deleting databases
- dropping databases
- databases [SQL Server], dropping
- database removal [SQL Server]
ms.assetid: 1fd8c0f5-03e1-449a-af45-b8cacb479d9c
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4c07c4a12f0e9f873266ba7862a7f291cc374151
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274320"
---
# <a name="delete-a-database"></a>Удаление базы данных
  В этом подразделе описывается, как удалить пользовательскую базу данных в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Предварительные требования](#Prerequisites)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Удаление базы данных с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After deleting a database](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Системные базы данных не могут быть удалены.  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Удалите все моментальные снимки базы данных, которые существуют для базы. Дополнительные сведения см. в разделе [Удаление моментального снимка базы данных (Transact-SQL)](drop-a-database-snapshot-transact-sql.md).  
  
-   Если база данных участвует в доставке журналов, удалите доставку журналов.  
  
-   Если база данных публикуется для репликации транзакций, опубликована или подписана на репликацию слиянием, удалите репликацию из базы данных.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Учтите возможность полного резервного копирования базы данных. Удаленную базу данных можно восстановить только с помощью резервной копии.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для выполнения инструкции DROP DATABASE пользователь должен, как минимум, иметь разрешение CONTROL на базу данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-a-database"></a>Удаление базы данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните **Базы данных**, щелкните правой кнопкой мыши удаляемую базу данных и затем нажмите кнопку **Удалить**.  
  
3.  Подтвердите, что выбрана верная база данных, а затем нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-delete-a-database"></a>Удаление базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В следующем примере удаляются базы данных `Sales` и `NewSales` .  
  
```tsql  
USE master ;  
GO  
DROP DATABASE Sales, NewSales ;  
GO  
```  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После удаления базы данных  
 Создание резервной копии базы данных **master** . Если необходимо восстановить базу данных **master** , любая база данных, удаленная с момента создания последней резервной копии базы данных **master** , останется в представлениях системного каталога и может вызвать сообщения об ошибках.  
  
## <a name="see-also"></a>См. также  
 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
