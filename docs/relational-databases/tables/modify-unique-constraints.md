---
title: Изменение ограничения уникальности | Документация Майкрософт
ms.custom: ''
ms.date: 10/12/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying constraints
- UNIQUE constraints [SQL Server], modifying
- constraints [SQL Server], modifying
- constraints [SQL Server], unique
ms.assetid: fddbdc9e-958b-4614-8e88-6ca205d64a4e
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 89786f2ed3a729408e18f8b77b4b1169794e42ea
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33007981"
---
# <a name="modify-unique-constraints"></a>Изменение ограничения уникальности
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Изменить ограничение уникальности в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Изменение ограничения уникальности с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-a-unique-constraint"></a>Изменение ограничения уникальности  
  
1.  В **обозревателе объектов**щелкните правой кнопкой мыши таблицу, содержащую ограничение уникальности, и выберите пункт **Конструктор**.  
  
2.  В меню **Конструктор таблиц** выберите пункт **Индексы и ключи...**  
  
3.  В диалоговом окне **Индексы и Ключи** в списке **Выбранный первичный/уникальный ключ или индекс**выберите ограничение, которое нужно изменить.  
  
4.  Выполните действие из следующей таблицы.  
  
    |Чтобы|Выполните следующее|  
    |--------|------------------------|  
    |Изменение столбца, с которым связано ограничение|1) В сетке в области **(Общие)** щелкните элемент **Столбцы** , затем нажмите кнопку с многоточием **(...)** справа от свойства.<br /><br /> 2) В диалоговом окне **Столбцы индекса** укажите для индекса новый столбец и (или) порядок сортировки.|  
    |Переименуйте ограничение|В сетке в области **Идентификатор**введите новое имя в поле **Имя** . Убедитесь, что новое имя не совпадает с именами в списке **Выбранный первичный/уникальный ключ или индекс** .|  
    |Установка параметра кластеризации|В сетке в области **Конструктор таблиц**выберите **Создать как кластеризованный** и нажмите кнопку "Да". Будет создан кластеризованный индекс, в противном случае — некластеризованный. Таблица может содержать только один кластеризованный индекс. Если кластеризованный индекс уже существует в этой таблице, то необходимо сначала отменить данный параметр в исходном индексе.|  
    |Установка коэффициента заполнения|В сетке в области **Конструктор таблиц**разверните категорию **Характеристики заполнения** и введите целое число от 0 до 100 в поле **Коэффициент заполнения** .|  
  
5.  В меню **Файл** выберите пункт **Сохранить***имя_таблицы*.  
  
##  <a name="TsqlProcedure"></a> **Изменение ограничения уникальности**  
  
 Чтобы изменить ограничение UNIQUE с помощью Transact-SQL, необходимо сначала удалить существующее ограничение, а затем создать его повторно с помощью нового определения. Дополнительные сведения см. в разделах [Delete Unique Constraints](../../relational-databases/tables/delete-unique-constraints.md) и [Create Unique Constraints](../../relational-databases/tables/create-unique-constraints.md).  
  
###  <a name="TsqlExample"></a>  
