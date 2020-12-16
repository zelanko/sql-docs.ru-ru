---
description: '&#x40;&#x40;SERVICENAME (Transact-SQL)'
title: '@@SERVICENAME (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@SERVICENAME_TSQL'
- '@@SERVICENAME'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@SERVICENAME function'
- names [SQL Server], registry keys
- registry keys [SQL Server]
ms.assetid: 5b0b35be-50ae-411d-a607-bf7464b73624
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||>=sql-server-linux-2017
ms.openlocfilehash: 04bcf15b50a106833fd7cf79bdd7d3cc388d74f2
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97481935"
---
# <a name="x40x40servicename-transact-sql"></a>&#x40;&#x40;SERVICENAME (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Возвращает имя раздела реестра, согласно которому запущен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если текущий экземпляр является экземпляром по умолчанию, функция @@SERVICENAME возвращает "MSSQLSERVER". Если же текущий экземпляр является именованным экземпляром, эта функция возвращает его имя.  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
@@SERVICENAME  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Типы возвращаемых данных
 **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускается в качестве службы с именем MSSQLServer.  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует использование процедуры `@@SERVICENAME`.  
  
```sql  
SELECT @@SERVICENAME AS 'Service Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Service Name                    
------------------------------  
MSSQLSERVER                     
```  
  
## <a name="see-also"></a>См. также  
 [Функции настройки (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Управление службами компонента Database Engine](../../database-engine/configure-windows/manage-the-database-engine-services.md)  
  
  
