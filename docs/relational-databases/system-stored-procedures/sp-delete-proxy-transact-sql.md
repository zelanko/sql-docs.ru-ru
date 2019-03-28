---
title: sp_delete_proxy (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_proxy
- sp_delete_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_proxy
- DROP PROXY statement
ms.assetid: 44a1db13-b7f2-4dab-a1b5-b8dafb41737c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dfd44237699c000447bbdfb2638d0d66550414dd
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528876"
---
# <a name="spdeleteproxy-transact-sql"></a>sp_delete_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет указанную учетную запись-посредник.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_proxy [ @proxy_id = ] id , [ @proxy_name = ] 'proxy_name'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @proxy_id = ] id` Идентификационный номер прокси-сервера для удаления. *Proxy_id* — **int**, значение по умолчанию NULL.  
  
`[ @proxy_name = ] 'proxy_name'` Имя прокси-сервера для удаления. *Proxy_name* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Либо **@proxy_name** или **@proxy_id** должен быть указан. Если указаны оба аргумента, они должны ссылаться на одну и ту же учетную запись-посредник, в противном случае хранимая процедура завершается ошибкой.  
  
 Если шаг задания ссылается на указанную учетную запись-посредник, хранимая процедура завершается с ошибкой.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_delete_proxy**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере производится удаление учетной записи-посредника `Catalog application proxy`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_proxy  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)  
  
  
