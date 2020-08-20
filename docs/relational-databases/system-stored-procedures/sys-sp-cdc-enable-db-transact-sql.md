---
description: sys.sp_cdc_enable_db (Transact-SQL)
title: sys. sp_cdc_enable_db (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_enable_db_TSQL
- sp_cdc_enable_db
- sys.sp_cdc_enable_db
- sys.sp_cdc_enable_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_cdc_enable_db
- change data capture [SQL Server], enabling databases
- sp_cdc_enable_db
ms.assetid: 176d83b3-493d-43cd-800e-aa123c3bdf17
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 810e39bf9c4ff4626bf957978a12d77df6e60d54
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485520"
---
# <a name="syssp_cdc_enable_db-transact-sql"></a>sys.sp_cdc_enable_db (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Включает систему отслеживания измененных данных для текущей базы данных. Эту процедуру необходимо выполнить в базе данных, чтобы для таблиц в этой базе можно было включить систему отслеживания измененных данных. Система отслеживания измененных данных регистрирует действия по вставке, обновлению и удалению, применяемые к таблицам, для которых включена система, предоставляя сведения об операциях изменения в легко обрабатываемом реляционном формате. Данные столбца, зеркально копирующего структуру столбцов отслеживаемой исходной таблицы, регистрируются для измененных строк вместе с метаданными, необходимыми для применения изменений к целевой среде.  
  
> [!IMPORTANT]
>  Система отслеживания измененных данных доступна не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_enable_db  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Система отслеживания измененных данных не может быть включена в [системных базах данных](../../relational-databases/databases/system-databases.md) или базах данных распространителя.  
  
 Процедура sys.sp_cdc_enable_db создает объекты отслеживания измененных данных, действующие в области базы данных, включая таблицы метаданных и триггеры DDL. Он также создает схему CDC и пользователя базы данных CDC и задает в столбце is_cdc_enabled для записи базы данных в представлении каталога [sys. databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) значение 1.  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в предопределенной роли сервера sysadmin.  
  
## <a name="examples"></a>Примеры  
 В следующем примере включается система отслеживания измененных данных.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_enable_db;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sys. sp_cdc_disable_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md)  
  
  
