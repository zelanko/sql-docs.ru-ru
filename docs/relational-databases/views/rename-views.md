---
title: "Переименование представлений | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-views
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- views [SQL Server], renaming
- renaming views
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1ca02551cedc64db57c833f57b428c715bf83fb4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="rename-views"></a>Переименование представлений
  Представление в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно переименовать, используя [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!WARNING]  
>  При переименовании представления фрагменты кода и приложения, использующие это представление, могут привести к сбою. Это касается других представлений, запросов, хранимых процедур, определяемых пользователем функций и клиентских приложений. Следует иметь в виду, что возникновение ошибок происходит каскадом.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Безопасность](#Security)  
  
-   **Переименование представления с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Продолжение:**  [после переименования представления](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
 Получение списка всех зависимостей в представлении. Все объекты, скрипты или приложения, которые ссылаются на представление, необходимо изменить в соответствии с новым именем представления. Дополнительные сведения см. в статье [Get Information About a View](../../relational-databases/views/get-information-about-a-view.md). Рекомендуется удалить представление и создать его повторно с новым именем вместо переименования. При повторном создании представления выполняется обновление сведений о зависимостях для объектов, на которые имеются ссылки в представлении.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется разрешение ALTER для SCHEMA или разрешение CONTROL для OBJECT, а также разрешение CREATE VIEW в базе данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-rename-a-view"></a>Переименование представления  
  
1.  В **обозревателе объектов**разверните базу данных, содержащую представление, которое необходимо переименовать, а затем разверните папку **Представление** .  
  
2.  Щелкните правой кнопкой мыши представление, которое нужно переименовать, и выберите пункт **Переименовать**.  
  
3.  Введите новое имя представления.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Переименование представления**  
  
 Хотя можно использовать **sp_rename** для изменения имени представления, рекомендуется удалить существующее представление, а затем повторно создать его с новым именем.  
  
 Дополнительные сведения см. в разделах [CREATE VIEW (Transact-SQL)](../../t-sql/statements/create-view-transact-sql.md) и [DROP VIEW (Transact-SQL)](../../t-sql/statements/drop-view-transact-sql.md).  
  
##  <a name="FollowUp"></a> Продолжение: после переименования представления  
 Убедитесь, что все объекты, скрипты и приложения, ссылающиеся на предыдущее имя представления, теперь используют новое имя.  
  
  
