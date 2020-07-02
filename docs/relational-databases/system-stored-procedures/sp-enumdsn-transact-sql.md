---
title: sp_enumdsn (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_enumdsn
- sp_enumdsn_TSQL
helpviewer_keywords:
- sp_enumdsn
ms.assetid: 171cbc7d-7406-4cb0-8602-9405243bfd1d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b7b69de24d9b92e82d624a694800988cdf74180c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85771105"
---
# <a name="sp_enumdsn-transact-sql"></a>sp_enumdsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Возвращает список имен всех определенных источников данных ODBC и OLE DB для сервера, работающего под определенной учетной записью [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Эта хранимая процедура выполняется на подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_enumdsn  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Имя источника данных**|**sysname**|Имя источника данных.|  
|**Описание**|**varchar (255)**|Описание источника данных.|  
|**Type**|**int**|Тип источника данных:<br /><br /> **1** = ODBC DSN<br /><br /> **3** = источник данных OLE DB|  
|**Имя поставщика**|**varchar (255)**|Имя поставщика OLE DB. Для ODBC DSN возвращается значение NULL.|  
  
## <a name="remarks"></a>Примечания  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] У каждой службы есть пользовательский контекст. Пользовательский контекст — это набор записей реестра, в который входят определения источников данных ODBC для пользователя. Пользовательскому контексту соответствует имя пользователя, под которым работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Например, если сервер работает в пользовательском контексте системной учетной записи, то все возвращаемые имена источников данных будут именами источников данных, связанных с системной учетной записью. Если сервер работает под частной пользовательской учетной записью, то будут возвращены имена источников данных только для частной учетной записи этого пользователя.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_enumdsn**.  
  
## <a name="see-also"></a>См. также  
 [sp_dsninfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dsninfo-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
