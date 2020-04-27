---
title: Переименование представлений | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- renaming views
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a0dfa9a95697c4bb1fcb2e4e5d3798f18e305e42
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211656"
---
# <a name="rename-views"></a>Переименование представлений
  Представление в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно переименовать, используя [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!WARNING]  
>  При переименовании представления фрагменты кода и приложения, использующие это представление, могут привести к сбою. Это касается других представлений, запросов, хранимых процедур, определяемых пользователем функций и клиентских приложений. Следует иметь в виду, что возникновение ошибок происходит каскадом.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Безопасность](#Security)  
  
-   **Переименование представления с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После переименования представления](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
 Получение списка всех зависимостей в представлении. Все объекты, скрипты или приложения, которые ссылаются на представление, необходимо изменить в соответствии с новым именем представления. Дополнительные сведения см. в статье [Get Information About a View](get-information-about-a-view.md). Рекомендуется удалить представление и создать его повторно с новым именем вместо переименования. При повторном создании представления выполняется обновление сведений о зависимостях для объектов, на которые имеются ссылки в представлении.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER для SCHEMA или разрешение CONTROL для OBJECT, а также разрешение CREATE VIEW в базе данных.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-rename-a-view"></a>Переименование представления  
  
1.  В **обозревателе объектов**разверните базу данных, содержащую представление, которое необходимо переименовать, а затем разверните папку **Представление** .  
  
2.  Щелкните правой кнопкой мыши представление, которое нужно переименовать, и выберите пункт **Переименовать**.  
  
3.  Введите новое имя представления.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Переименование представления**  
  
 Хотя можно использовать **sp_rename** для изменения имени представления, рекомендуется удалить существующее представление, а затем повторно создать его с новым именем.  
  
 Дополнительные сведения см. в разделах [CREATE VIEW (Transact-SQL)](/sql/t-sql/statements/create-view-transact-sql) и [DROP VIEW (Transact-SQL)](/sql/t-sql/statements/drop-view-transact-sql).  
  
##  <a name="follow-up-after-renaming-a-view"></a><a name="FollowUp"></a> Дальнейшие действия. После переименования представления  
 Убедитесь, что все объекты, скрипты и приложения, ссылающиеся на предыдущее имя представления, теперь используют новое имя.  
  
  
