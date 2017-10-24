---
title: "Создание ПОСТАВЩИКА служб ШИФРОВАНИЯ (Transact-SQL) | Документы Microsoft"
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
- CREATE_CRYPTOGRAPHIC_TSQL
- CRYPTOGRAPHIC PROVIDER
- PROVIDER_TSQL
- CREATE CRYPTOGRAPHIC
- CREATE CRYPTOGRAPHIC PROVIDER
- CRYPTOGRAPHIC_PROVIDER_TSQL
- CREATE_CRYPTOGRAPHIC_PROVIDER_TSQL
- PROVIDER
dev_langs:
- TSQL
helpviewer_keywords:
- 33085 (Database Engine error)
- CREATE CRYPTOGRAPHIC PROVIDER statement
- 33032 (Database Engine error)
ms.assetid: 059a39a6-9d32-4d3f-965b-0a1ce75229c7
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9a7252786522ef4e0b4206db06d7dc8aa76cf308
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-cryptographic-provider-transact-sql"></a>CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает поставщика служб шифрования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на основе поставщика расширенного управления ключами.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE CRYPTOGRAPHIC PROVIDER provider_name   
    FROM FILE = path_of_DLL  
```  
  
## <a name="arguments"></a>Аргументы  
 *provider_name*  
 Имя поставщика расширенного управления ключами.  
  
 *path_of_DLL*  
 Путь к DLL-библиотеке, реализующей интерфейс расширенного управления ключами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При использовании **соединитель SQL Server для хранилища ключей Microsoft Azure** расположение по умолчанию — **"C:\Program Files\Microsoft SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll '**.  
  
## <a name="remarks"></a>Замечания  
 Все ключи, созданные поставщиком, ссылаются на поставщик по его идентификатору GUID. Идентификатор GUID сохраняются во всех версиях DLL-библиотеки.  
  
 Библиотека, реализующая интерфейс SQLEKM, должна быть подписана цифровой подписью с использованием любого сертификата. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнит проверку подписи. Сюда входят цепочка сертификатов, который должен иметь установлен в корень **доверенных корневых сертификатов центров** расположение в системе Windows. Если подпись не проверяется правильно, инструкции CREATE CRYPTOGRAPHIC PROVIDER завершится ошибкой. Дополнительные сведения о сертификатах и цепочках сертификатов см. в разделе [SQL Server сертификаты и асимметричные ключи](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  
  
 Когда поставщик EKM DLL-библиотек реализует не все необходимые методы, то инструкция CREATE CRYPTOGRAPHIC PROVIDER может вернуть ошибку 33085:  
  
 `One or more methods cannot be found in cryptographic provider library '%.*ls'.`  
  
 Если файл заголовка, используемый для создания поставщика EKM DLL-библиотек, устарел, то инструкция CREATE CRYPTOGRAPHIC PROVIDER может вернуть ошибку 33032:  
  
 `SQL Crypto API version '%02d.%02d' implemented by provider is not supported. Supported version is '%02d.%02d'.`  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение CONTROL SERVER или членство в **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается поставщик служб шифрования вызывается `SecurityProvider` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из DLL-файла. DLL-файл называется `c:\SecurityProvider\SecurityProvider_v1.dll` и устанавливается на сервере. Сначала необходимо установить на сервере сертификат поставщика.  
  
```  
-- Install the provider  
CREATE CRYPTOGRAPHIC PROVIDER SecurityProvider  
    FROM FILE = 'C:\SecurityProvider\SecurityProvider_v1.dll';  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенное управление ключами &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [ALTER CRYPTOGRAPHIC PROVIDER (Transact-SQL)](../../t-sql/statements/alter-cryptographic-provider-transact-sql.md)   
 [DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL)](../../t-sql/statements/drop-cryptographic-provider-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Расширенное управление ключами с помощью хранилища ключей Azure &#40;SQL Server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
  

