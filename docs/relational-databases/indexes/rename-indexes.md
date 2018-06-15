---
title: Переименование индексов | Документация Майкрософт
ms.custom: ''
ms.date: 02/17/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- renaming indexes
- index names [SQL Server]
- indexes [SQL Server], renaming
ms.assetid: d3d612a1-ea1b-4d99-85d2-0a2ad54f4b0e
caps.latest.revision: 27
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9756cc3ab6ef292860648f846b4be481a54376b7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32938279"
---
# <a name="rename-indexes"></a>Переименование индексов
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  В этом разделе описывается процедура переименования индекса в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. При переименовании индекса его текущее имя заменяется на предоставленное новое. Указанное имя должно быть уникальным в рамках таблицы или представления. Например, две таблицы могут иметь индекс с именем **XPK_1**, но для одной таблицы не может быть двух индексов с именем **XPK_1**. Нельзя создавать индекс с тем же именем, что и существующий отключенный индекс. Переименование индекса не приводит к его перестройке.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Переименование индекса с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 При создании ограничения PRIMARY KEY или UNIQUE для таблицы автоматически создается индекс с таким же именем, что и имя ограничения. Поскольку имена индексов должны быть уникальны в пределах таблицы, нельзя создавать или переименовывать индекс, присваивая ему такое же имя, что и у существующего в таблице ограничения PRIMARY KEY или UNIQUE.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется разрешение ALTER для индекса.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-rename-an-index-by-using-the-table-designer"></a>Переименование индекса при помощи конструктора таблиц  
  
1.  В обозревателе объектов щелкните знак «плюс», чтобы развернуть базу данных, содержащую таблицу, в которой необходимо переименовать индекс.  
  
2.  Чтобы развернуть папку **Таблицы** , щелкните значок «плюс».  
  
3.  Щелкните правой кнопкой мыши таблицу, в которой нужно переименовать индекс, и выберите пункт **Конструктор**.  
  
4.  В меню **Конструктор таблиц** выберите пункт **Индексы и ключи**.  
  
5.  В текстовом поле **Выбранный первичный (уникальный) ключ или индекс** выберите индекс, который нужно переименовать.  
  
6.  В сетке выберите **Имя** и введите новое имя в текстовое поле.  
  
7.  Щелкните **Закрыть**.  
  
8.  В меню **Файл** выберите команду **Сохранить***имя_таблицы*.  
  
#### <a name="to-rename-an-index-by-using-object-explorer"></a>Переименование индекса при помощи обозревателя объектов  
  
1.  В обозревателе объектов щелкните знак «плюс», чтобы развернуть базу данных, содержащую таблицу, в которой необходимо переименовать индекс.  
  
2.  Чтобы развернуть папку **Таблицы** , щелкните значок «плюс».  
  
3.  Щелкните знак «плюс», чтобы развернуть таблицу, в которой необходимо переименовать индекс.  
  
4.  Чтобы развернуть папку **Индексы** , щелкните знак «плюс» (+).  
  
5.  Щелкните правой кнопкой мыши индекс, который нужно переименовать, и выберите пункт **Переименовать**.  
  
6.  Введите новое имя индекса и нажмите клавишу ВВОД.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-rename-an-index"></a>Переименование индекса  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    --Renames the IX_ProductVendor_VendorID index on the Purchasing.ProductVendor table to IX_VendorID.   
  
    EXEC sp_rename N'Purchasing.ProductVendor.IX_ProductVendor_VendorID', N'IX_VendorID', N'INDEX';   
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_rename (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md).  
  
  
