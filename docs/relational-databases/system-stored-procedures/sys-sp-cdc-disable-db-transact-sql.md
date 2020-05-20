---
title: sys. sp_cdc_disable_db (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_disable_db
- sys.sp_cdc_disable_db_TSQL
- sp_cdc_disable_db_TSQL
- sys.sp_cdc_disable_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_disable_db
- sys.sp_cdc_disable_db
- change data capture [SQL Server], disabling databases
ms.assetid: 420fb99e-e60f-445b-b568-da96471f1e8f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 16ce8ad7a388a7f1e0d492c186bf4aaddf6acbcd
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832558"
---
# <a name="syssp_cdc_disable_db-transact-sql"></a>sys.sp_cdc_disable_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отключает систему отслеживания измененных данных в текущей базе данных. Система отслеживания измененных данных доступна не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с по [текущей версии](https://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
sys.sp_cdc_disable_db  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sys. sp_cdc_disable_db** отключает отслеживание измененных данных для всех таблиц в базе данных, которые в данный момент включены. Удаляются все системные объекты, относящиеся к системе отслеживания измененных данных, например таблицы изменений, задания, хранимые процедуры и функции. Столбцу **is_cdc_enabled** для записи базы данных в представлении каталога [sys. databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) присваивается значение 0.  
  
> [!NOTE]  
>  Если для базы данных определено несколько экземпляров системы отслеживания в то время, когда система отслеживания измененных данных отключена, то продолжительное выполнение какой-либо транзакции может вызвать ошибку в работе sys.sp_cdc_disable_db. Эту проблему можно избежать, отключив отдельные экземпляры системы отслеживания с помощью таблицы sys.sp_cdc_disable_table перед запуском процедуры sys.sp_cdc_disable_db.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере отключается система отслеживания измененных данных для таблицы `AdventureWorks2012`.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_disable_db;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sys. sp_cdc_enable_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md)   
 [sys. sp_cdc_disable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-table-transact-sql.md)  
  
  
