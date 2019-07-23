---
title: ALTER CRYPTOGRAPHIC PROVIDER (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 04/20/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER_CRYPTOGRAPHIC_PROVIDER_TSQL
- ALTER CRYPTOGRAPHIC PROVIDER
- ALTER_CRYPTOGRAPHIC_TSQL
- ALTER CRYPTOGRAPHIC
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER CRYPTOGRAPHIC PROVIDER
ms.assetid: 876b6348-fb29-49e1-befc-4217979f6416
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b27695eba9f1092b09d147c373877a9b44789497
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065905"
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
  
## <a name="remarks"></a>Примечания  
 Если поставщик изменяет DLL-файл, используемый для реализации расширенного управления ключами в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], нужно использовать инструкцию ALTER CRYPTOGRAPHIC PROVIDER.  
  
 Если путь к DLL-файлу обновляется инструкцией ALTER CRYPTOGRAPHIC PROVIDER, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет следующие действия.  
-   Отключает поставщик.  
-   Проверяет подлинность подписи DLL-библиотеки, а также то, что ее идентификатор GUID совпадает с тем, который записан в каталоге.  
-   Обновляет версию DLL-библиотеки в каталоге.  
  

Если для поставщика расширенного управления ключами установлено значение DISABLE, то любые попытки использовать этот поставщик с инструкциями шифрования для новых соединений завершается ошибкой.  
  
Перед отключением поставщика необходимо закрыть все сеансы, использующие его.  
  
Если DLL-библиотека поставщика расширенного управления ключами не реализует все необходимые методы, то инструкция ALTER CRYPTOGRAPHIC PROVIDER может вернуть ошибку 33085:  
  
 `One or more methods cannot be found in cryptographic provider library '%.*ls'.`  
  
Если файл заголовка, используемый для создания поставщика расширенного управления ключами DLL-библиотек, устарел, то инструкция ALTER CRYPTOGRAPHIC PROVIDER может вернуть ошибку 33032:  
  
 `SQL Crypto API version '%02d.%02d' implemented by provider is not supported. Supported version is '%02d.%02d'.`  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение CONTROL для поставщика служб шифрования.  
  
## <a name="examples"></a>Примеры  
 В следующем примере происходит замена DLL-библиотеки на более новую версию для поставщика служб шифрования `SecurityProvider` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта новая версия имеет имя `c:\SecurityProvider\SecurityProvider_v2.dll` и установлена на сервере. Сначала необходимо установить на сервере сертификат поставщика.  
  
1. Отключите поставщик для выполнения обновления. Будут завершены все открытые сеансы шифрования.  
```  
ALTER CRYPTOGRAPHIC PROVIDER SecurityProvider   
DISABLE;  
GO  
```  

2. Обновите DLL-файл поставщика. Идентификатор GUID должен быть тем же, что и в предыдущей версии, но версия может отличаться.  
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
  
## <a name="see-also"></a>См. также  
 [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL)](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL)](../../t-sql/statements/drop-cryptographic-provider-transact-sql.md)   
 [CREATE SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Расширенное управление ключами с помощью хранилища ключей Azure (SQL Server)](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
  
