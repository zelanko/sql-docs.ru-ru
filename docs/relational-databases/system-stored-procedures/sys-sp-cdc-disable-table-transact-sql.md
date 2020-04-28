---
title: sys. sp_cdc_disable_table (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_disable_table
- sp_cdc_disable_table
- sys.sp_cdc_disable_table_TSQL
- sp_cdc_disable_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_disable_table
- sys.sp_cdc_disable_table
- change data capture [SQL Server], disabling tables
ms.assetid: da2156c0-504e-4d76-b9a0-4448becf9bda
author: rothja
ms.author: jroth
ms.openlocfilehash: 693c449679433b733cfc3a45e2bbedf3f1d92185
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68106512"
---
# <a name="syssp_cdc_disable_table-transact-sql"></a>sys.sp_cdc_disable_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отключает систему отслеживания измененных данных для указанной исходной таблицы, а также отключает экземпляр отслеживания в текущей базе данных. Система отслеживания измененных данных доступна не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список функций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживаемых различными выпусками, см. [в разделе функции, поддерживаемые различными выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_disable_table   
  [ @source_schema = ] 'source_schema' ,   
  [ @source_name = ] 'source_name'  
  [ , [ @capture_instance = ] 'capture_instance' | 'all' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @source_schema = ] 'source\_schema'`Имя схемы, в которой содержится исходная таблица. Аргумент *source_schema* имеет тип **sysname**, не имеет значения по умолчанию и не может иметь значение null.  
  
 *source_schema* должен существовать в текущей базе данных.  
  
`[ @source_name = ] 'source\_name'`Имя исходной таблицы, из которой система отслеживания измененных данных должна быть отключена. Аргумент *source_name* имеет тип **sysname**, не имеет значения по умолчанию и не может иметь значение null.  
  
 *source_name* должен существовать в текущей базе данных.  
  
`[ @capture_instance = ] 'capture\_instance' | 'all'`Имя экземпляра отслеживания, который необходимо отключить для указанной исходной таблицы. *capture_instance* имеет тип **sysname** и не может иметь значение null.  
  
 Если указан параметр "ALL", все экземпляры отслеживания, определенные для *source_name* , отключаются.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sys. sp_cdc_disable_table** удаляет таблицу изменений системы отслеживания измененных данных и системные функции, связанные с указанной исходной таблицей и экземпляром отслеживания. Он удаляет все строки, связанные с указанным экземпляром отслеживания, из системных таблиц системы отслеживания измененных данных и задает для столбца **is_tracked_by_cdc** для записи таблицы в представлении каталога [sys. Tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) значение 0.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных **db_owner** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере отключается система отслеживания измененных данных для таблицы `HumanResources.Employee`.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_disable_table   
    @source_schema = N'HumanResources',   
    @source_name = N'Employee',  
    @capture_instance = N'HumanResources_Employee';  
```  
  
## <a name="see-also"></a>См. также:  
 [sys. sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)  
  
  
