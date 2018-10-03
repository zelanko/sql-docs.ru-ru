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
ms.openlocfilehash: 556d6f5a7513f08867c73ba26369861d9e960688
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810312"
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
 [  **@source_schema=** ] **"***source_schema***"**  
 Имя схемы, в которой содержится исходная таблица. *source_schema* — **sysname**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
 *source_schema* должен существовать в текущей базе данных.  
  
 [  **@source_name=** ] **"***source_name***"**  
 Имя исходной таблицы, из которой можно отключить систему отслеживания измененных данных. *source_name* — **sysname**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
 *source_name* должен существовать в текущей базе данных.  
  
 [  **@capture_instance=** ] **"***capture_instance***"** | **"** все **"**  
 Имя экземпляра системы отслеживания, отключаемого в указанной исходной таблице. *capture_instance* — **sysname** и не может иметь значение NULL.  
  
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
  
  
