---
title: DROP CERTIFICATE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/18/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP CERTIFICATE
- DROP_CERTIFICATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], removing
- removing certificates
- dropping certificates
- DROP CERTIFICATE statement
- deleting certificates
ms.assetid: 5704aa04-68a3-4b29-b62b-8868af487817
caps.latest.revision: 37
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 813b67a5a4af3adba211eb12ca40733b5dc5c0a1
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38002896"
---
# <a name="drop-certificate-transact-sql"></a>DROP CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  Удаляет сертификат из базы данных.  
  
> [!IMPORTANT]  
>  Резервная копия сертификата, используемого для шифрования базы данных, должна быть сохранена, даже если она больше не включена в базе данных. Даже если база данных больше не зашифрована, части журнала транзакций могут по-прежнему оставаться защищенными, а для некоторых операций будет требоваться сертификат до выполнения полного резервного копирования базы данных. Сертификат также потребуется для восстановления из резервных копий, созданных в то время, когда база данных была зашифрована.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP CERTIFICATE certificate_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *certificate_name*  
 Уникальное имя, под которым сертификат известен в базе данных.  
  
## <a name="remarks"></a>Примечания  
 Сертификаты можно удалять только при условии, что с ними не связано никаких сущностей.  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения CONTROL для сертификата.  
  
## <a name="examples"></a>Примеры  
 В следующем примере сертификат `Shipping04` удаляется из базы данных `AdventureWorks`.  
  
```  
USE AdventureWorks2012;  
DROP CERTIFICATE Shipping04;  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере удаляется сертификат `Shipping04`.  
  
```
USE master;  
DROP CERTIFICATE Shipping04;  
```  
  
## <a name="see-also"></a>См. также  
 [BACKUP CERTIFICATE (Transact-SQL)](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE (Transact-SQL)](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)