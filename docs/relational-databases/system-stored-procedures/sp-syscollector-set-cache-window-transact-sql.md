---
title: sp_syscollector_set_cache_window (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_set_cache_window
- sp_syscollector_set_cache_window_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_set_cache_window stored procedure
- data collector [SQL Server], stored procedures
ms.assetid: 660f2749-392f-46bf-89f3-27764d848507
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80462381e058c4cb9107aa4ac07138e42d27e677
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68010629"
---
# <a name="spsyscollectorsetcachewindow-transact-sql"></a>sp_syscollector_set_cache_window (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Устанавливает, сколько раз будет выполняться попытка передачи данных в случае ошибки. Повторная попытка передачи при сбое снижает угрозу потери собранных данных.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_set_cache_window [ @cache_window = ] cache_window   
```  
  
## <a name="arguments"></a>Аргументы  
 [ @cache_window =] *cache_window*  
 Количество повторных передач данных в хранилище данных управления без потери данных в случае ошибки. *cache_window* — **int** со значением по умолчанию 1. *cache_window* может иметь одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|-1|Кэширует все данные из предыдущих неудавшихся передач.|  
|0|Не кэширует данные из неудавшейся передачи.|  
|*n*|Кэширует данные из n предыдущих неудавшихся передач, где *n* > = 1.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Необходимо отключить сборщик данных перед изменением конфигурации окна кэша. Если включен сборщик данных, эта хранимая процедура завершится с ошибкой. Дополнительные сведения см. в разделе [включить или отключить сбор данных](../../relational-databases/data-collection/enable-or-disable-data-collection.md), и [Управление сбором данных](../../relational-databases/data-collection/manage-data-collection.md).  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой процедуры требуется членство в предопределенной роли базы данных dc_admin (с разрешением EXECUTE).  
  
## <a name="examples"></a>Примеры  
 В этом примере показано отключение сборщика данных, настройка окна кэша для сохранения данных из трех предыдущих неудачных передач и последующее включение для сборщика данных.  
  
```sql  
USE msdb;  
GO  
EXECUTE dbo.sp_syscollector_disable_collector;  
GO  
EXECUTE dbo.sp_syscollector_set_cache_window 3;  
GO  
EXECUTE dbo.sp_syscollector_enable_collector;  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_syscollector_set_cache_directory (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-set-cache-directory-transact-sql.md)  
  
  
