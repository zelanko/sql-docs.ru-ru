---
title: DROP MASTER KEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP MASTER KEY
- DROP_MASTER_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing Database Master Keys
- database master key [SQL Server], removing
- encryption [SQL Server], Database Master Key
- DROP MASTER KEY statement
- cryptography [SQL Server], Database Master Key
- dropping Database Master Keys
- deleting Database Master Keys
ms.assetid: 5ccef797-408f-4964-80da-965d8e1ccba7
caps.latest.revision: 34
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e28dadb61d1d2b5237f08dbafa782be58d0155d8
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43108340"
---
# <a name="drop-master-key-transact-sql"></a>DROP MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Удаляет главный ключ из текущей базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP MASTER KEY  
```  
  
## <a name="arguments"></a>Аргументы  
 Для этой инструкции не нужны никакие аргументы.  
  
## <a name="remarks"></a>Remarks  
 Если какой-либо закрытый ключ в базе данных защищен главным ключом, удаление закончится с ошибкой.  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения CONTROL для базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется главный ключ для базы данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
DROP MASTER KEY;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В приведенном ниже примере удаляется главный ключ.  
  
```  
USE master;  
DROP MASTER KEY;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE MASTER KEY (Transact-SQL)](../../t-sql/statements/create-master-key-transact-sql.md)   
 [OPEN MASTER KEY (Transact-SQL)](../../t-sql/statements/open-master-key-transact-sql.md)   
 [CLOSE MASTER KEY (Transact-SQL)](../../t-sql/statements/close-master-key-transact-sql.md)   
 [BACKUP MASTER KEY (Transact-SQL)](../../t-sql/statements/backup-master-key-transact-sql.md)   
 [RESTORE MASTER KEY (Transact-SQL)](../../t-sql/statements/restore-master-key-transact-sql.md)   
 [ALTER MASTER KEY (Transact-SQL)](../../t-sql/statements/alter-master-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

