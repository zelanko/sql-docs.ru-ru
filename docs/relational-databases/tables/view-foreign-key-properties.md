---
title: Просмотр свойств внешнего ключа | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- foreign keys [SQL Server], attributes
- displaying foreign keys attributes
- viewing foreign keys attributes
ms.assetid: b0e57cb7-9b26-4b96-b76a-1f59f5f498c5
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bb42d6630d5dd4632a9674c2b783aa2059f80cda
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "72905799"
---
# <a name="view-foreign-key-properties"></a>Просмотр свойств внешнего ключа
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Просматривать атрибуты внешнего ключа связи в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Просмотр атрибутов внешнего ключа таблицы с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a>Просмотр атрибутов внешнего ключа связей в таблице  
  
1.  Откройте в конструкторе таблиц таблицу, содержащую внешний ключ, который нужно просмотреть. Щелкните правой кнопкой мыши конструктор таблиц и выберите в контекстном меню пункт **Связи** .  
  
2.  В диалоговом окне **Связи внешних ключей** выберите связь, свойства которой нужно просмотреть.  

 Если внешние ключевые столбцы связаны с первичным ключом, столбцы первичных ключей можно идентифицировать в **конструкторе таблиц** по символу первичного ключа в селекторе строк.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a>Просмотр атрибутов внешнего ключа связей в таблице  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В приведенном далее примере возвращаются сведения обо всех внешних ключах и их свойствах для таблицы `HumanResources.Employee` из образца базы данных.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT   
        f.name AS foreign_key_name  
       ,OBJECT_NAME(f.parent_object_id) AS table_name  
       ,COL_NAME(fc.parent_object_id, fc.parent_column_id) AS constraint_column_name  
       ,OBJECT_NAME (f.referenced_object_id) AS referenced_object  
       ,COL_NAME(fc.referenced_object_id, fc.referenced_column_id) AS referenced_column_name  
       ,is_disabled  
       ,delete_referential_action_desc  
       ,update_referential_action_desc  
    FROM sys.foreign_keys AS f  
    INNER JOIN sys.foreign_key_columns AS fc   
       ON f.object_id = fc.constraint_object_id   
    WHERE f.parent_object_id = OBJECT_ID('HumanResources.Employee');  
    ```  
  
 Дополнительные сведения см. в разделе [sys.foreign_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-foreign-keys-transact-sql.md) и [sys.foreign_key_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-foreign-key-columns-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  
