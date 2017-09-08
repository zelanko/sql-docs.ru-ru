---
title: "PWDCOMPARE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PWDCOMPARE
- PWDCOMPARE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sa account
- passwords [SQL Server], blank
- PWDCOMPARE function [Transact-SQL]
ms.assetid: 5f84ff9e-c1ec-46aa-8501-50f854ebcc3a
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6aadde33d6d1ee1404170197c32ab77ade2dbfad
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="pwdcompare-transact-sql"></a>PWDCOMPARE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Хэширует пароль и сравнивает хэш с хэшем существующего пароля. Функция PWDCOMPARE может использоваться для поиска пустых паролей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или распространенных простых паролей.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PWDCOMPARE ( 'clear_text_password'  
   , password_hash   
   [ , version ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *clear_text_password* **"**  
 Незашифрованный пароль. *clear_text_password* — **sysname** (**nvarchar(128)**).  
  
 *password_hash*  
 Хэш шифрования пароля. *password_hash* — **varbinary(128)**.  
  
 *Версия*  
 Устаревший параметр, который можно присвоить значение 1, если *password_hash* представляет значение для имени входа из более ранней, чем [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] которое было перенесено в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии, но никогда не преобразуются в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] системы. *версия* — **int**.  
  
> [!CAUTION]  
>  Этот параметр предназначен для обеспечения обратной совместимости, однако он пропускается, так как теперь большие двоичные объекты хэшей паролей содержат собственные описания версий. [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
 Возвращает 1, если хэш *clear_text_password* соответствует *password_hash* параметр и 0, если это не так.  
  
## <a name="remarks"></a>Замечания  
 Функция PWDCOMPARE — это не угроза устойчивости хэшей паролей, потому что этот же самый тест можно было бы выполнить, если попытаться использовать для входа пароль, заданный как первый параметр.  
  
 **PWDCOMPARE** не может использоваться с паролями пользователей автономной базы данных. Какой-либо эквивалент для автономной базы данных отсутствует.  
  
## <a name="permissions"></a>Permissions  
 Функция PWDENCRYPT общедоступна.  
  
 Для просмотра столбца password_hash column представления sys.sql_logins требуется разрешение CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-identifying-logins-that-have-no-passwords"></a>A. Выявление имен входа, у которых нет паролей  
 В следующем примере выявляются имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], у которых нет паролей.  
  
```  
SELECT name FROM sys.sql_logins   
WHERE PWDCOMPARE('', password_hash) = 1 ;  
```  
  
### <a name="b-searching-for-common-passwords"></a>Б. Поиск распространенных простых паролей  
 Для поиска распространенных простых паролей, которые требуется выявить и изменить, задайте пароль как первый параметр. Например, можно выполнить следующую инструкцию для поиска пароля, заданного как `password`.  
  
```  
SELECT name FROM sys.sql_logins   
WHERE PWDCOMPARE('password', password_hash) = 1 ;  
```  
  
## <a name="see-also"></a>См. также:  
 [PWDENCRYPT &#40; Transact-SQL &#41;](../../t-sql/functions/pwdencrypt-transact-sql.md)   
 [Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
