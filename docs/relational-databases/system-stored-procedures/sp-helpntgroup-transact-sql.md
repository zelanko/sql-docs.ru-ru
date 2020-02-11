---
title: sp_helpntgroup (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpntgroup
- sp_helpntgroup_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpntgroup
ms.assetid: 02b4f7c1-480a-436c-8bae-7a2488be45d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: fcc4a42307ccb11923460bb9c01c5cf7bdd8f8df
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68133680"
---
# <a name="sp_helpntgroup-transact-sql"></a>sp_helpntgroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выводит сведения о группах Windows, имеющих учетные записи в текущей базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpntgroup [ [ @ntname= ] 'name' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @ntname = ] 'name'`— Имя группы Windows. Аргумент *Name* имеет тип **sysname**и значение по умолчанию NULL. *имя* должно быть допустимой группой Windows с доступом к текущей базе данных. Если параметр *Name* не указан, в выходные данные включаются все группы Windows с доступом к текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**NTGroupName**|**имеет sysname**|Имя группы Windows.|  
|**NTGroupId**|**smallint**|Идентификатор группы (ID).|  
|**ТРАНСЛЯЦИЮ**|**varbinary (85)**|Идентификатор безопасности (SID) **нтграупнаме**.|  
|**хасдбакцесс**|**int**|1 = группа Windows имеет разрешение на доступ к базе данных.|  
  
## <a name="remarks"></a>Remarks  
 Чтобы просмотреть список [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ролей в текущей базе данных, используйте **sp_helprole**.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли **Public** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере выводится список групп Windows, имеющих доступ к текущей базе данных.  
  
```  
EXEC sp_helpntgroup;  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_helprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_revokedbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
