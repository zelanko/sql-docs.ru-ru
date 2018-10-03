---
title: sp_unsetapprole (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_unsetapprole_TSQL
- sp_unsetapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unsetapprole
ms.assetid: 4c4033d3-1a34-4dfb-835d-e3293d1a442d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 52a3c04463eb4384d48e333e6d81097a33fd9ac1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47716602"
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
 Указывает куки-файл, который был создан при активации роли приложения. Файл cookie создается с [sp_setapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md). **varbinary(8000)**.  
  
> [!NOTE]  
>  Параметр **OUTPUT** куки-файла для инструкции **sp_setapprole** в настоящее время описан в документации как **varbinary(8000)** , что верно определяет его максимальную длину. Однако текущая реализация возвращает параметр **varbinary(50)**. Приложения должны продолжать зарезервировать **varbinary(8000)** таким образом, приложение для правильной работы в случае увеличения размера куки в будущем выпуске.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) и 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 После приложение активации роли с помощью **sp_setapprole**, роль остается активной, пока пользователь отключается от сервера или выполняет **sp_unsetapprole**.  
  
 Обзор ролей приложения, см. в разделе [ролей приложения](../../relational-databases/security/authentication-access/application-roles.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **открытый** и знание куки-файл сохраняется при активации роли приложения.  
  
## <a name="examples"></a>Примеры  
  
### <a name="activating-an-application-role-with-a-cookie-then-reverting-to-the-previous-context"></a>Активация роли приложения с помощью куки-файла, затем возврат к предыдущему контексту.  
 В следующем примере включается роль приложения `Sales11` с паролем `fdsd896#gfdbfdkjgh700mM` и создается куки-файл. В примере возвращает имя текущего пользователя, а затем возвращается к исходному контексту, выполнив **sp_unsetapprole**.  
  
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
  
## <a name="see-also"></a>См. также  
 [sp_setapprole (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/create-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/drop-application-role-transact-sql.md)  
  
  
