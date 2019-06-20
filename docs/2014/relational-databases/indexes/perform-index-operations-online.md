---
title: Выполнение операций с индексами в сети | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index online operations [SQL Server]
- online index operations
- ONLINE option
ms.assetid: 1e43537c-bf67-4db3-9908-3cb45c6fdaa1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b9eceaff8ea7fee16eac3afef8bdc560d7fb1642
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63036226"
---
# <a name="perform-index-operations-online"></a>Выполнение операции с индексами в сети
  В этом разделе описывается создание, перестроение и удаление индексов в режиме «в сети» в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр ONLINE разрешает одновременный доступ пользователей к базовой таблице или данным кластеризованного индекса и всем связанным некластеризованным индексам во время выполнения этих операций с индексами. Например, пока пользователь перестраивает кластеризованный индекс, он и другие пользователи могут продолжать обновление базовых данных и осуществлять к ним запросы. Если операции языка описания данных DDL (DDL), такие как построение или перестроение кластеризованного индекса, выполняются в режиме «вне сети», то они удерживают монопольные блокировки на базовые данные и связанные индексы. Это предотвращает изменение базовых данных и осуществление запросов к ним до завершения операции с индексами.  
  
> [!NOTE]  
>  Операции с индексами в сети доступны не во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Для перестроения индекса в режиме «в сети» используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Рекомендуется выполнять операции с индексами в сети в производственной среде, работающей 24 часа в сутки и семь дней в неделю, когда имеется насущная необходимость одновременных действий пользователей во время выполнения операций с индексами.  
  
-   Параметр ONLINE доступен в следующих инструкциях языка [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
    -   [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql)  
  
    -   [ALTER INDEX](/sql/t-sql/statements/alter-index-transact-sql)  
  
    -   [DROP INDEX](/sql/t-sql/statements/drop-index-transact-sql)  
  
    -   [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) (чтобы добавить или удалить ограничения UNIQUE или PRIMARY KEY с параметром индекса CLUSTERED)  
  
-   Дополнительные ограничения и ограничения, касающиеся создания, восстановления или удаления индексов в режиме "в сети", см. в разделе [Инструкции по операциям с индексами в сети](guidelines-for-online-index-operations.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER для таблицы или представления.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-rebuild-an-index-online"></a>Перестроение индекса в режиме «в сети»  
  
1.  В обозревателе объектов щелкните знак «плюс», чтобы развернуть базу данных, содержащую таблицу, в которой необходимо перестроить индекс в режиме «в сети».  
  
2.  Разверните папку **Таблицы**.  
  
3.  Щелкните знак «плюс», чтобы развернуть таблицу, в которой необходимо перестроить индекс в режиме «в сети».  
  
4.  Разверните папку **Индексы** .  
  
5.  Щелкните правой кнопкой мыши индекс, который нужно перестроить в режиме "в сети", и выберите **Свойства**.  
  
6.  В разделе **Выбор страницы**щелкните **Параметры**.  
  
7.  Выберите свойство **Разрешить обработку DML в сети**и выберите из списка значение **True** .  
  
8.  Нажмите кнопку **ОК**.  
  
9. Щелкните правой кнопкой мыши индекс, который нужно перестроить в режиме "в сети", и выберите пункт **Перестроить**.  
  
10. В диалоговом окне **Перестроение индексов** убедитесь, что нужный индекс приведен в сетке **Индексы для перестройки** и нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-rebuild-or-drop-an-index-online"></a>Создание, перестроение и удаление индекса в режиме «в сети»  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В примере перестраивается существующий индекс в режиме «в сети»  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee  
    REBUILD WITH (ONLINE = ON);  
    GO  
    ```  
  
     В следующем примере кластеризованный индекс удаляется в режиме в сети и результирующая таблица (куча) перемещается в файловую группу `NewGroup` с использованием предложения `MOVE TO` . Представления каталога `sys.indexes`, `sys.tables`и `sys.filegroups` запрашиваются для проверки размещения индекса и таблицы в файловых группах до и после перемещения.  
  
     [!code-sql[IndexDDL#DropIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/dropindex.sql#dropindex4)]  
  
 Дополнительные сведения см. в статье [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql).  
  
  
