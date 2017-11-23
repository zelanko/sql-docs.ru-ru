---
title: "ALTER CRYPTOGRAPHIC PROVIDER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/20/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_CRYPTOGRAPHIC_PROVIDER_TSQL
- ALTER CRYPTOGRAPHIC PROVIDER
- ALTER_CRYPTOGRAPHIC_TSQL
- ALTER CRYPTOGRAPHIC
dev_langs: TSQL
helpviewer_keywords: ALTER CRYPTOGRAPHIC PROVIDER
ms.assetid: 876b6348-fb29-49e1-befc-4217979f6416
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fe377a27978cdae372a7bfc8545d7cad1f514820
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="alter-cryptographic-provider-transact-sql"></a>ALTER CRYPTOGRAPHIC PROVIDER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет поставщика служб шифрования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на основе поставщика расширенного управления ключами.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER CRYPTOGRAPHIC PROVIDER provider_name   
    [ FROM FILE = path_of_DLL ]  
    ENABLE | DISABLE  
```  
  
## <a name="arguments"></a>Аргументы  
 *provider_name*  
 Имя поставщика расширенного управления ключами.  
  
 *Path_of_DLL*  
 Путь к DLL-библиотеке, реализующей интерфейс расширенного управления ключами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ENABLE | DISABLE  
 Включает или отключает поставщик.  
  
## <a name="remarks"></a>Замечания  
 Если поставщик изменяет DLL-файл, используемый для реализации расширенного управления ключами в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], нужно использовать инструкцию ALTER CRYPTOGRAPHIC PROVIDER.  
  
 Если путь к DLL-файлу обновляется инструкцией ALTER CRYPTOGRAPHIC PROVIDER, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет следующие действия.  
-   Отключает поставщик.  
-   Проверяет подлинность подписи DLL-библиотеки, а также то, что ее идентификатор GUID совпадает с тем, который записан в каталоге.  
-   Обновляет версию DLL-библиотеки в каталоге.  
  

Если для поставщика расширенного управления ключами установлено значение DISABLE, то любые попытки использовать этот поставщик с инструкциями шифрования для новых соединений завершатся ошибкой.  
  
Перед отключением поставщика необходимо закрыть все сеансы, использующие его.  
  
Если DLL-библиотека поставщика расширенного управления ключами не реализует все необходимые методы, то инструкция ALTER CRYPTOGRAPHIC PROVIDER может вернуть ошибку 33085:  
  
 `One or more methods cannot be found in cryptographic provider library '%.*ls'.`  
  
Если файл заголовка, используемый для создания поставщика расширенного управления ключами DLL-библиотек, устарел, то инструкция ALTER CRYPTOGRAPHIC PROVIDER может вернуть ошибку 33032:  
  
 `SQL Crypto API version '%02d.%02d' implemented by provider is not supported. Supported version is '%02d.%02d'.`  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение CONTROL для поставщика служб шифрования.  
  
## <a name="examples"></a>Примеры  
 В следующем примере изменяется поставщика служб шифрования, вызывается `SecurityProvider` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], до более новой версии DLL-файл. Эта новая версия имеет имя `c:\SecurityProvider\SecurityProvider_v2.dll` и установлен на сервере. Сначала необходимо установить на сервере сертификат поставщика.  
  
1. Отключите поставщик для выполнения обновления. Это нарушит все открытые сеансы служб шифрования.  
```  
ALTER CRYPTOGRAPHIC PROVIDER SecurityProvider   
DISABLE;  
GO  
```  

2. Обновление поставщика DLL-файл. Идентификатор GUID должно быть таким же, как предыдущая, но версия может отличаться.  
```  
ALTER CRYPTOGRAPHIC PROVIDER SecurityProvider  
FROM FILE = 'c:\SecurityProvider\SecurityProvider_v2.dll';  
GO  
```  

3. Включите обновленный поставщик.   
```  
ALTER CRYPTOGRAPHIC PROVIDER SecurityProvider   
ENABLE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенное управление ключами &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL)](../../t-sql/statements/drop-cryptographic-provider-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Расширенное управление ключами с помощью хранилища ключей Azure &#40;SQL Server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
  
