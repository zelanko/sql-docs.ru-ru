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
manager: craigg
ms.openlocfilehash: 024d7c4a043dbc4801d5eb39fe7b05d27ef7c2b5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65943229"
---
# <a name="pwdencrypt-transact-sql"></a>PWDENCRYPT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
  
