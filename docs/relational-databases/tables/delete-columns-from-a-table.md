---
title: "Удаление столбцов из таблицы | Документация Майкрософт"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [SQL Server], deleting
- removing columns
- deleting columns
- dropping columns
ms.assetid: 0d8f6e4f-bc71-4fa3-8615-74249c8e072d
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: HT
ms.sourcegitcommit: 621185759462020bca20985c3133c93814a1f333
ms.openlocfilehash: ef0c4b8b66af5dfc46c836fc8c18734609b1301a
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="delete-columns-from-a-table"></a>Удаление столбцов из таблицы
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  В этом разделе приведены инструкции по удалению столбцов таблиц в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!CAUTION]  
>  При удалении столбца из таблицы этот столбец и все содержащиеся в нем данные удаляются из базы данных. Отменить это действие невозможно.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Удаление столбца из таблицы с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 Нельзя удалить столбец, имеющий ограничение CHECK. В первую очередь необходимо удалить ограничение.  
  
 Удалить столбец, имеющий ограничения PRIMARY KEY, FOREIGN KEY или другие зависимости можно только с использованием конструктора таблиц. При использовании обозревателя объектов или [!INCLUDE[tsql](../../includes/tsql-md.md)]необходимо в первую очередь удалить зависимости столбца.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-columns-by-using-object-explorer"></a>Удаление столбцов с помощью обозревателя объектов  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  В **обозревателе объектов** найдите таблицу, из которой нужно удалить столбцы, и разверните ее, чтобы отобразить имена столбцов. 

3.  Щелкните правой кнопкой мыши столбец, который необходимо удалить, и выберите команду **Удалить**.  
  
3.  В диалоговом окне **Удаление объекта** нажмите кнопку **ОК**.  
  
 Если столбец содержит ограничения или другие зависимости, то в диалоговом окне **Удаление объекта** будет отображено сообщение об ошибке. Чтобы устранить проблему, удалите упомянутые ограничения.  
  
#### <a name="to-delete-columns-by-using-table-designer"></a>Удаление столбцов с использованием конструктора таблиц  
  
1.  В **обозревателе объектов**щелкните правой кнопкой мыши таблицу, из которой необходимо удалить столбцы, и выберите пункт **Конструктор**.  
  
2.  Щелкните правой кнопкой мыши столбец, который надо удалить, и выберите из контекстного меню пункт **Удалить столбец** .  
  
3.  Если столбец участвует в связи (FOREIGN KEY или PRIMARY KEY), то будет выдано сообщение с запросом на подтверждение удаления выбранных столбцов и их связей. Выберите **Да**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-delete-columns"></a>Удаление столбцов  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.doc_exb DROP COLUMN column_b ;  
    ```  
  
 Если столбец содержит ограничения или другие зависимости, то будет возвращено сообщение об ошибке. Чтобы устранить проблему, удалите упомянутые ограничения.  
  
 Дополнительные примеры см. в статье [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md).  
  
##  <a name="FollowUp"></a>  

