---
description: Изменение первичных ключей
title: Изменение первичных ключей | Документация Майкрософт
ms.custom: ''
ms.date: 07/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying primary keys
- primary keys [SQL Server], modifying
ms.assetid: 8e2a15ba-1cd1-4408-b860-16c3ee37d635
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f69001aa9bdc4785c992f019807b411f00b755b2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473059"
---
# <a name="modify-primary-keys"></a>Изменение первичных ключей
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Изменить первичный ключ в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Изменить первичный ключ таблицы можно, изменив порядок столбцов, имя индекса, параметр кластеризации или коэффициент заполнения.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Изменение первичного ключа с использованием:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-a-primary-key"></a>Изменение первичного ключа  
  
1.  Откройте в конструкторе таблиц таблицу, первичный ключ которой необходимо изменить, правой кнопкой мыши щелкните конструктор таблиц и выберите пункт **Индексы и ключи** в контекстном меню.  
  
2.  В диалоговом окне **Индексы/ключи** выберите индекс первичного ключа из списка **Выберите первичный/уникальный ключ или индекс** .  
  
3.  Выполните действие из следующей таблицы.  
  
    |Кому|Выполните следующее|  
    |--------|------------------------|  
    |Переименование первичного ключа|Введите новое имя в поле **Имя** . Убедитесь, что новое имя не совпадает с именами в списке **Выбранный первичный/уникальный ключ или индекс** .|  
    |Установка параметра кластеризации|Для создания кластеризованного индекса для первичного ключа укажите **Создать как CLUSTERED**и выберите нужный параметр из раскрывающегося списка. Таблица может содержать только один кластеризованный индекс. Если этот параметр недоступен для выбранного индекса, то сначала снимите этот флажок в существующем кластеризованном индексе.<br /><br /> Если этот параметр не выбран, создается уникальный некластеризованный индекс.|  
    |Установка коэффициента заполнения|Разверните категорию **Характеристики заполнения** и введите целое число от 0 до 100 в поле **Коэффициент заполнения** . Дополнительные сведения о коэффициентах заполнения и их использовании см. в разделе [Укажите коэффициент заполнения для индекса](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).|  
    |Изменение порядка столбцов|Выберите свойство **Столбцы**и нажмите кнопку с многоточием **(...)** справа от свойства. В диалоговом окне  **Столбцы индекса** удалите столбцы из первичного ключа. Затем снова добавьте эти столбцы в необходимом порядке. Чтобы удалить столбец из ключа, просто удалите имя столбца из списка имен **Столбец** .|  
  
4.  В меню **Файл** выберите команду **Сохранить**_имя_таблицы_.  

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение первичного ключа**  
  
 Чтобы изменить ограничение PRIMARY KEY с использованием Transact-SQL, необходимо сначала удалить существующее ограничение PRIMARY KEY, а затем создать новое с другим определением. Дополнительные сведения см. в разделах [Delete Primary Keys](../../relational-databases/tables/delete-primary-keys.md) и [Create Primary Keys](../../relational-databases/tables/create-primary-keys.md).  
  
###  <a name="TsqlExample"></a>  
