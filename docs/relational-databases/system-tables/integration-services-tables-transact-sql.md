---
title: В службах Integration Services таблицы (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- SQL Server Integration Services system tables
- system tables [SQL Server], Integration Services
- system tables [Integration Services]
- SSIS, system tables
ms.assetid: 683b181b-0091-4a9c-86db-bc577af43cec
caps.latest.revision: 21
author: douglasl
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fc5df46211b3de92b054fea4120d9b7c884a0ccb
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33259624"
---
# <a name="integration-services-tables-transact-sql"></a>Таблицы служб Integration Services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Подразделы в этом разделе содержат описания системных таблиц базы данных msdb, которые хранят информацию, используемую службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
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
  
  
