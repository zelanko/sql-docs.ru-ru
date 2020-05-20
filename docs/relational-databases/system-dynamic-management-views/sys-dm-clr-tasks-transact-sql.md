---
title: sys. dm_clr_tasks (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_clr_tasks
- sys.dm_clr_tasks_TSQL
- dm_clr_tasks
- dm_clr_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_tasks dynamic management view
ms.assetid: 462b9061-09fa-4858-9707-03d6cc19c769
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8a4726504794c70909664633168bfc3730ff65c7
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824710"
---
# <a name="sysdm_clr_tasks-transact-sql"></a>sys.dm_clr_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает по одной строке для всех задач среды CLR, выполняющихся в данный момент. Пакет языка [!INCLUDE[tsql](../../includes/tsql-md.md)], который содержит ссылку на процедуру среды CLR, создает отдельную задачу для выполнения всего управляемого кода в пакете. Несколько инструкций пакета, которые требуют выполнения управляемого кода, используют одну и ту же задачу среды CLR. Задача среды CLR отвечает за поддержку объектов и состояний, относящихся к выполнению управляемого кода, а также за обмен данными между экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и средой CLR.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|Адрес задачи среды CLR.|  
|**sos_task_address**|**varbinary(8)**|Адрес базовой задачи пакета языка [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|**appdomain_address**|**varbinary(8)**|Адрес домена приложений, в котором выполняется задача.|  
|**state**|**nvarchar(128)**|Текущее состояние задачи.|  
|**abort_state**|**nvarchar(128)**|Указывает на состояние прерывания (если выполнение задачи было отменено). Существует несколько состояний, связанных с прерыванием задач.|  
|**type**|**nvarchar(128)**|Тип задачи.|  
|**affinity_count**|**int**|Родственность задачи.|  
|**forced_yield_count**|**int**|Количество раз, когда задача принудительно выдавала результат.|  
  
## <a name="permissions"></a>Разрешения  

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные со средой CLR &#40;языке Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  

