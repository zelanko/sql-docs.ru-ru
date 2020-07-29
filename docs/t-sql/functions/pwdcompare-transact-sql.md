---
title: PWDCOMPARE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ad59b8d81641999da674ca73db696c2f0c3ce1ef
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87111868"
---
# <a name="pwdcompare-transact-sql"></a>PWDCOMPARE (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Хэширует пароль и сравнивает хэш с хэшем существующего пароля. Функция PWDCOMPARE может использоваться для поиска пустых паролей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или распространенных простых паролей.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
PWDCOMPARE ( 'clear_text_password'  
   , password_hash   
   [ , version ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 **'** *clear_text_password* **'**  
 Незашифрованный пароль. Аргумент *clear_text_password* имеет тип **sysname** (**nvarchar(128)** ).  
  
 *password_hash*  
 Хэш шифрования пароля. Аргумент *password_hash* имеет тип **varbinary(128)** .  
  
 *version*  
 Устаревший параметр, который может быть установлен в значение 1, если *password_hash* представляет значение для имени входа из версии ранее [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], которое было перенесено в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более позднюю версию, но так и не было преобразовано в систему [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Аргумент *version* имеет тип **int**.  
  
> [!CAUTION]  
>  Этот параметр предназначен для обеспечения обратной совместимости, однако он пропускается, так как теперь большие двоичные объекты хэшей паролей содержат собственные описания версий. [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
 Возвращает значение 1, если хэш параметра *clear_text_password* совпадает со значением параметра *password_hash*, или значение 0 в противном случае.  
  
## <a name="remarks"></a>Remarks  
 Функция PWDCOMPARE — это не угроза устойчивости хэшей паролей, потому что этот же самый тест можно было бы выполнить, если попытаться использовать для входа пароль, заданный как первый параметр.  
  
 **PWDCOMPARE** нельзя использовать с паролями пользователей автономных баз данных. Какой-либо эквивалент для автономной базы данных отсутствует.  
  
## <a name="permissions"></a>Разрешения  
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
 [PWDENCRYPT (Transact-SQL)](../../t-sql/functions/pwdencrypt-transact-sql.md)   
 [Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
