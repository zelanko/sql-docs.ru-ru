---
title: Удаление хранимой процедуры | Документация Майкрософт
description: Узнайте, как в SQL Server 2019 (15.x) удалить хранимую процедуру с помощью SQL Server Management Studio или Transact-SQL.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- removing stored procedures
- stored procedures [SQL Server], deleting
- deleting stored procedures
ms.assetid: 232dbf4d-392a-406f-af3a-579518cd8e46
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 742b0e7f3631f5cf262ff6e20bdc64f1ba7bea7f
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475315"
---
# <a name="delete-a-stored-procedure"></a>Удаление хранимой процедуры
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
    
##  <a name="this-topic-describes-how-to-delete-a-stored-procedure-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> В этом разделе описывается, как удалить хранимую процедуру [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Перед началом работы**  [Ограничения](#Restrictions), [Безопасность](#Security)  
  
-   **Удаление хранимой процедуры с использованием:**  [среды SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 Удаление процедуры может вызвать ошибку в зависимых объектах и в скриптах, если эти объекты и скрипты не обновляются для отражения удаления процедуры. Тем не менее, если вместо удаленной создать другую хранимую процедуру с тем же именем и параметрами, хранимые процедуры, которые на нее ссылаются, будут обрабатываться успешно. Дополнительные сведения см. в разделе [Просмотр зависимостей хранимой процедуры](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на схему, которой принадлежит процедура, или разрешение CONTROL на процедуру.  
  
##  <a name="how-to-delete-a-stored-procedure"></a><a name="Procedures"></a> Удаление хранимой процедуры  
 Можно использовать один из следующих способов:  
  
-   [Среда SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Удаление процедуры в обозревателе объектов**  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Последовательно разверните узел **Базы данных**, базу данных, которой принадлежит процедура, и узел **Программирование**.  
  
3.  Разверните **Хранимые процедуры**, щелкните правой кнопкой мыши удаляемую процедуру, затем нажмите кнопку **Удалить**.  
  
4.  Для просмотра объектов, зависящих от хранимой процедуры, нажмите **Показать зависимости**.  
  
5.  Подтвердите, что выбрана нужная процедура, и нажмите кнопку **ОК**.  
  
6.  Удалите ссылки на процедуру из зависимых объектов и скриптов.  

###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Удаление процедуры в редакторе запросов**  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните **Базы данных**, разверните базу данных, к которой относится процедура, или с помощью панели инструментов выберите базу данных из списка доступных.  
  
3.  В меню «Файл» выберите команду **Создать запрос**.  
  
4.  Получите имя хранимой процедуры для удаления из текущей базы данных. В обозревателе объектов разверните узел **Программирование** , затем **Хранимые процедуры**. Также можно выполнить следующую инструкцию в редакторе запросов.  
  
    ```sql  
    SELECT name AS procedure_name   
        ,SCHEMA_NAME(schema_id) AS schema_name  
        ,type_desc  
        ,create_date  
        ,modify_date  
    FROM sys.procedures;  
    ```  
  
5.  Скопируйте и вставьте следующий пример в редактор запросов и введите имя хранимой процедуры, которую нужно удалить из текущей базы данных.  
  
    ```sql  
    DROP PROCEDURE <stored procedure name>;  
    GO  
    ```  
  
6.  Удалите ссылки на процедуру из зависимых объектов и скриптов.  
  
## <a name="see-also"></a>См. также:  
 [Создание хранимой процедуры](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [Изменение хранимой процедуры](../../relational-databases/stored-procedures/modify-a-stored-procedure.md)   
 [Изменение имени хранимой процедуры](../../relational-databases/stored-procedures/rename-a-stored-procedure.md)   
 [Просмотр определения хранимой процедуры](../../relational-databases/stored-procedures/view-the-definition-of-a-stored-procedure.md)   
 [Просмотр зависимостей хранимой процедуры](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md)   
 [DROP PROCEDURE (Transact-SQL)](../../t-sql/statements/drop-procedure-transact-sql.md)  
  
  
