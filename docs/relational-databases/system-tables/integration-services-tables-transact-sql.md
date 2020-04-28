---
title: Таблицы Integration Services (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- SQL Server Integration Services system tables
- system tables [SQL Server], Integration Services
- system tables [Integration Services]
- SSIS, system tables
ms.assetid: 683b181b-0091-4a9c-86db-bc577af43cec
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 61379adc04eddaf276fae37879674b63833b76e7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67990137"
---
# <a name="integration-services-tables-transact-sql"></a>Таблицы служб Integration Services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В подразделах этого раздела описываются системные таблицы базы данных msdb, в которых хранятся сведения, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]используемые.  
  
## <a name="in-this-section"></a>В этом разделе  
 [sysssislog](../../relational-databases/system-tables/sysssislog-transact-sql.md)  
 Содержит одну строку для каждой записи журнала, формируемой пакетом служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] во время выполнения.  
  
 Эта таблица используется, только если пакеты используют регистратор [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [sysssispackagefolders](../../relational-databases/system-tables/sysssispackagefolders-transact-sql.md)  
 Содержит одну строку для каждой логической папки, которую служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] использует для организации пакетов. Значения столбцов определяют связь родитель-потомок между вложенными папками.  
  
> [!NOTE]  
>  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] хранимые пакеты отображаются в иерархическом представлении после подключения пользователя к службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [sysssispackages](../../relational-databases/system-tables/sysssispackages-transact-sql.md)  
 Содержит одну строку для каждого пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Эта таблица используется, только если пакеты хранятся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
