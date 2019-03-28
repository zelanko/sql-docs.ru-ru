---
title: sys.sp_cdc_disable_table (Transact-SQL) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 0b1c2f30758987c902e5610ef3fa9f8b26809889
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533747"
---
# <a name="sysspcdcdisabletable-transact-sql"></a>sys.sp_cdc_disable_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отключает систему отслеживания измененных данных для указанной исходной таблицы, а также отключает экземпляр отслеживания в текущей базе данных. Система отслеживания измененных данных доступна не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_disable_table   
  [ @source_schema = ] 'source_schema' ,   
  [ @source_name = ] 'source_name'  
  [ , [ @capture_instance = ] 'capture_instance' | 'all' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @source_schema = ] 'source\_schema'` — Это имя схемы, в которой содержится исходная таблица. *source_schema* — **sysname**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
 *source_schema* должен существовать в текущей базе данных.  
  
`[ @source_name = ] 'source\_name'` — Имя исходной таблицы, из которой система отслеживания измененных данных требуется отключить. *source_name* — **sysname**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
 *source_name* должен существовать в текущей базе данных.  
  
`[ @capture_instance = ] 'capture\_instance' | 'all'` — Имя экземпляра отслеживания, чтобы отключить для указанной исходной таблице. *capture_instance* — **sysname** и не может иметь значение NULL.  
  
 Если выбрано «все», все экземпляры, определенные для отслеживания *source_name* отключены.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 **sys.sp_cdc_disable_table** удаляет измененных данных изменить таблицу, а также системные функции, связанные с указанной исходной таблицы и экземпляр отслеживания. Удаляются все строки, связанные с указанным экземпляром отслеживания из таблицы система захвата данных и наборы **is_tracked_by_cdc** столбец для записи таблицы [sys.tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) представление каталога значение 0.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **db_owner** предопределенной роли базы данных.  
  
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
  
## <a name="see-also"></a>См. также  
 [sys.sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)  
  
  
