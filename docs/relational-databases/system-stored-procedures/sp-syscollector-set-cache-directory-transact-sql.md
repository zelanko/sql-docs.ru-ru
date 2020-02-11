---
title: sp_syscollector_set_cache_directory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_set_cache_directory_TSQL
- sp_syscollector_set_cache_directory
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_set_cache_directory stored procedure
ms.assetid: df56d5a5-8961-494f-a745-d752ca63805a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 03236c2882cad61e42ffa0fcdeb322d4ada53c2a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "76910047"
---
# <a name="sp_syscollector_set_cache_directory-transact-sql"></a>sp_syscollector_set_cache_directory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Указывает каталог, где хранятся собранные данные на компьютере до их передачи в хранилище данных управления.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_set_cache_directory [ @cache_directory = ] 'cache_directory'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @cache_directory = ] 'cache_directory'`Каталог в файловой системе, где собранные данные временно хранятся. *cache_directory* имеет тип **nvarchar (255)** и значение по умолчанию NULL. Если значение данного параметра не указано, для хранения временной информации используется папка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 Необходимо отключить сборщик данных перед изменением конфигурации каталога кэша. Если включен сборщик данных, эта хранимая процедура завершится с ошибкой. Дополнительные сведения см. в разделе [Включение или отключение сбора данных](../../relational-databases/data-collection/enable-or-disable-data-collection.md)и [Управление сбором данных](../../relational-databases/data-collection/manage-data-collection.md).  
  
 Указанный каталог не обязательно должен существовать во время выполнения sp_syscollector_set_cache_directory; Однако данные не могут быть успешно кэшированы и отправлены, пока каталог не будет создан. Рекомендуется создать каталог до выполнения этой хранимой процедуры.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой процедуры требуется членство в предопределенной роли базы данных dc_admin (с разрешением EXECUTE).  
  
## <a name="examples"></a>Примеры  
 В следующем примере отключается сборщик данных, устанавливается каталог кэша для сборщика данных `D:\tempdata`, а затем включается сборщик данных.  
  
```sql  
USE msdb;  
GO  
EXECUTE dbo.sp_syscollector_disable_collector;  
GO  
EXEC dbo.sp_syscollector_set_cache_directory N'D:\tempdata';  
GO  
EXECUTE dbo.sp_syscollector_enable_collector;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры сборщика данных &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [sp_syscollector_set_cache_window &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-set-cache-window-transact-sql.md)  
  
  
