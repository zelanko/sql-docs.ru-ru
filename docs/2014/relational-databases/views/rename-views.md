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
ms.openlocfilehash: 9fa559d0aaf1f805f7885b931bcce7f78b012701
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48063834"
---
# <a name="rename-views"></a>Переименование представлений
  Представление в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно переименовать, используя [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!WARNING]  
>  При переименовании представления фрагменты кода и приложения, использующие это представление, могут привести к сбою. Это касается других представлений, запросов, хранимых процедур, определяемых пользователем функций и клиентских приложений. Следует иметь в виду, что возникновение ошибок происходит каскадом.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Предварительные требования](#Prerequisites)  
  
     [безопасность](#Security)  
  
-   **Переименование представления с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After renaming a view](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
 Получение списка всех зависимостей в представлении. Все объекты, скрипты или приложения, которые ссылаются на представление, необходимо изменить в соответствии с новым именем представления. Дополнительные сведения см. в статье [Get Information About a View](get-information-about-a-view.md). Рекомендуется удалить представление и создать его повторно с новым именем вместо переименования. При повторном создании представления выполняется обновление сведений о зависимостях для объектов, на которые имеются ссылки в представлении.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER для SCHEMA или разрешение CONTROL для OBJECT, а также разрешение CREATE VIEW в базе данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-rename-a-view"></a>Переименование представления  
  
1.  В **обозревателе объектов**разверните базу данных, содержащую представление, которое необходимо переименовать, а затем разверните папку **Представление** .  
  
2.  Щелкните правой кнопкой мыши представление, которое нужно переименовать, и выберите пункт **Переименовать**.  
  
3.  Введите новое имя представления.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Переименование представления**  
  
 Хотя можно использовать **sp_rename** для изменения имени представления, рекомендуется удалить существующее представление, а затем повторно создать его с новым именем.  
  
 Дополнительные сведения см. в разделах [CREATE VIEW (Transact-SQL)](/sql/t-sql/statements/create-view-transact-sql) и [DROP VIEW (Transact-SQL)](/sql/t-sql/statements/drop-view-transact-sql).  
  
##  <a name="FollowUp"></a> Продолжение: после переименования представления  
 Убедитесь, что все объекты, скрипты и приложения, ссылающиеся на предыдущее имя представления, теперь используют новое имя.  
  
  
