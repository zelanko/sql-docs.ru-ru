---
title: Удаление таблиц (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- table deletions [SQL Server]
- deleting tables
- removing tables
- dropping tables
ms.assetid: ca6aa3e9-9885-44c3-bafc-aec441fd97ec
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 61a9cb34d8cd4bafdfbdcd44bb8fdbd973205847
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190937"
---
# <a name="delete-tables-database-engine"></a>Удаление таблиц (компонент Database Engine)
  Удалить таблицу из базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!CAUTION]  
>  Каждое удаление таблицы следует тщательно планировать. Если на таблицу ссылаются существующие запросы, представления, определяемые пользователем функции, хранимые процедуры или программы, то удаление сделает эти объекты недействительными.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Удаление таблицы с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Инструкцию DROP TABLE нельзя использовать для удаления таблицы, на которую ссылается ограничение FOREIGN KEY. Сначала следует удалить ссылающееся ограничение FOREIGN KEY или ссылающуюся таблицу. Если и ссылающаяся таблица, и таблица, содержащая первичный ключ, удаляются с помощью одной инструкции DROP TABLE, ссылающаяся таблица должна быть первой в списке.  
  
-   При удалении таблицы относящиеся к ней правила и значения по умолчанию теряют привязку, а любые связанные с таблицей ограничения или триггеры автоматически удаляются. Если таблица будет создана заново, нужно будет заново привязать все правила и значения по умолчанию, заново создать триггеры и добавить необходимые ограничения.  
  
-   При удалении таблицы, содержащей `varbinary (max)` столбец с атрибутом FILESTREAM, данные, хранящиеся в файловой системе, не будут удалены.  
  
-   Инструкции DROP TABLE и CREATE TABLE нельзя выполнять для одной таблицы в одном пакете. В противном случае может произойти непредвиденная ошибка.  
  
-   Любые представления или хранимые процедуры, которые ссылаются на удаляемую таблицу, необходимо явно удалить или изменить, чтобы убрать ссылку на таблицу.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на схему, к которой принадлежит эта таблица, разрешение CONTROL для этой таблицы или членство в предопределенной роли базы данных **db_ddladmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-a-table-from-the-database"></a>Удаление таблицы из базы данных  
  
1.  В обозревателе объектов выберите таблицу, которую необходимо удалить.  
  
2.  Щелкните таблицу правой кнопкой мыши и в контекстном меню выберите **Удалить** .  
  
3.  Появится окно подтверждения удаления. Нажмите кнопку **Да**.  
  
    > [!NOTE]  
    >  При удалении таблицы автоматически удаляются все связи с ней.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-delete-a-table-in-query-editor"></a>Удаление таблицы в редакторе запросов  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    DROP TABLE dbo.PurchaseOrderDetail;  
  
    ```  
  
 Дополнительные сведения см. в статье [DROP TABLE (Transact-SQL)](/sql/t-sql/statements/drop-table-transact-sql).  
  
  
