---
title: sp_validname (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_validname
- sp_validname_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_validname
ms.assetid: d51c53c2-1332-407f-b725-4983f2e710eb
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c559c8a6af6add669e1cc4630b7bcfc9fc0aacc2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67936738"
---
# <a name="sp_validname-transact-sql"></a>sp_validname (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Проверяет на правильность имена идентификаторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Все недвоичные и ненулевые данные, включая данные в Юникоде, которые могут храниться с использованием типов данных **nchar**, **nvarchar**или **ntext** , принимаются как допустимые символы для имен идентификаторов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_validname [@name =] 'name'   
     [, [@raise_error =] raise_error]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @name = ] 'name'`Имя [идентификаторов](../../relational-databases/databases/database-identifiers.md) , для которых проверяется допустимость. Аргумент *Name* имеет тип **sysname**и не имеет значения по умолчанию. *имя* не может иметь значение null, не может быть пустой строкой и не может содержать двоичный символ.  
  
`[ @raise_error = ] raise_error`Указывает, следует ли вызывать ошибку. *raise_error* имеет **бит**и значение по умолчанию 1. Это означает, что ошибки будут отображаться. 0 приводит к тому, что сообщения об ошибках появляться не будут.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли **Public** .  
  
## <a name="see-also"></a>См. также:  
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Типы данных &#40;&#41;Transact-SQL](../../t-sql/data-types/data-types-transact-sql.md)   
 [&#41;&#40;языка Transact-SQL на языке NCHAR](../../t-sql/functions/nchar-transact-sql.md)   
 [nchar и nvarchar &#40;Transact-SQL&#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)   
 [&#41;Transact-SQL на языке ntext, Text и Image &#40;](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
