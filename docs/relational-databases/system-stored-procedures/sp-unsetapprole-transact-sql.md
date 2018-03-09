---
title: "sp_unsetapprole (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_unsetapprole_TSQL
- sp_unsetapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unsetapprole
ms.assetid: 4c4033d3-1a34-4dfb-835d-e3293d1a442d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c85e56a002f6f6105e9bc9a05dab48d61c07dbc0
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spunsetapprole-transact-sql"></a>sp_unsetapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Деактивирует роль приложения и возвращает к предыдущему контексту безопасности.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_unsetapprole @cookie   
```  
  
## <a name="arguments"></a>Аргументы  
 **@cookie**  
 Указывает куки-файл, который был создан при активации роли приложения. Файл cookie создается с [sp_setapprole &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md). **varbinary(8000)**.  
  
> [!NOTE]  
>  Параметр **OUTPUT** куки-файла для инструкции **sp_setapprole** в настоящее время описан в документации как **varbinary(8000)** , что верно определяет его максимальную длину. Однако текущая реализация возвращает параметр **varbinary(50)**. Приложения должны продолжать зарезервировать **varbinary(8000)** , чтобы приложение продолжает работать неправильно, если в будущем выпуске увеличения размера возвращаемых куки-файлов.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) и 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 После применения активации роли с помощью **sp_setapprole**, роль остается активной, пока пользователь отключается от сервера или выполняет **sp_unsetapprole**.  
  
 Обзор ролей приложения см. в разделе [ролей приложения](../../relational-databases/security/authentication-access/application-roles.md).  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в **открытый** и знание куки-файла, сохраняются при активации роли приложения.  
  
## <a name="examples"></a>Примеры  
  
### <a name="activating-an-application-role-with-a-cookie-then-reverting-to-the-previous-context"></a>Активация роли приложения с помощью куки-файла, затем возврат к предыдущему контексту.  
 В следующем примере включается роль приложения `Sales11` с паролем `fdsd896#gfdbfdkjgh700mM` и создается куки-файл. В примере возвращается имя текущего пользователя, а затем происходит возврат к исходному контексту с помощью выполнения **sp_unsetapprole**.  
  
```  
DECLARE @cookie varbinary(8000);  
EXEC sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.   
GO   
```  
  
## <a name="see-also"></a>См. также:  
 [sp_setapprole &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Безопасность хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [СОЗДАТЬ РОЛЬ приложения &#40; Transact-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/drop-application-role-transact-sql.md)  
  
  
