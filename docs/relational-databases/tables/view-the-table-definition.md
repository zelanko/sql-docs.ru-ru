---
title: Просмотр определения таблицы | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- showing table properties
- displaying table properties
- tables [SQL Server], properties
- viewing table properties
ms.assetid: 1865fb7c-f480-4100-9007-df5364cd002a
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3e2feaf8e9d8d45b986961d5d49f5b230fd2a301
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43098778"
---
# <a name="view-the-table-definition"></a>Просмотр определения таблицы
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Отобразить свойства таблицы можно в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Отображение свойств таблицы с использованием:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Просматривать свойства таблицы может только владелец таблицы или лицо, получившее разрешения на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-show-table-properties-in-the-properties-window"></a>Отображение свойств таблицы в окне «Свойства»  
  
1.  В обозревателе объектов выберите таблицу, для которой необходимо просмотреть свойства.  
  
2.  Щелкните таблицу правой кнопкой мыши и в контекстном меню выберите пункт **Свойства** . Дополнительные сведения см. в разделе [Свойства таблицы — SSMS](../../relational-databases/tables/table-properties-ssms.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-show-table-properties"></a>Отображение свойств таблицы  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В примере возвращаются все столбцы из представления каталога `sys.tables` для указанного объекта.  
  
    ```  
    SELECT * FROM sys.tables  
    WHERE object_id = 1973582069;  
  
    ```  
  
 Дополнительные сведения см. в разделе [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  
