---
title: PWDENCRYPT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PWDENCRYPT
- PWDENCRYPT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PWDENCRYPT function [Transact-SQL]
ms.assetid: 333e9a43-1099-4b9b-b941-4b0b016f47f3
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e6e6ebf976f7fc475761685090064d14d00f6f75
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892136"
---
# <a name="pwdencrypt-transact-sql"></a>PWDENCRYPT (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает хэш пароля [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для входного значения, использующего текущую версию алгоритма хэширования пароля.  
  
 PWDENCRYPT — это устаревшая функция, которая может не поддерживаться в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Используйте вместо нее [HASHBYTES](../../t-sql/functions/hashbytes-transact-sql.md). HASHBYTES предоставляет больше алгоритмов хэширования.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PWDENCRYPT ( 'password' )  
```  
  
## <a name="arguments"></a>Аргументы  
 *password*  
 Подлежит ли пароль шифрованию. Аргумент *password* имеет тип **sysname**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **varbinary(128)**  
  
## <a name="permissions"></a>Разрешения  
 Функция PWDENCRYPT общедоступна.  
  
## <a name="see-also"></a>См. также:  
 [Функции безопасности (Transact-SQL)](../../t-sql/functions/security-functions-transact-sql.md)   
 [PWDCOMPARE (Transact-SQL)](../../t-sql/functions/pwdcompare-transact-sql.md)  
  
  
