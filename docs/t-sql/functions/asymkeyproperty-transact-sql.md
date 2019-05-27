---
title: ASYMKEYPROPERTY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ASYMKEYPROPERTY_TSQL
- ASYMKEYPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- ASYMKEYPROPERTY
ms.assetid: a30581f2-e1b1-4996-93e6-527ff96b7c42
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: de7e95ab26102c0b3bbe1e33c57ae9491a5b9a2c
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65945886"
---
# <a name="asymkeyproperty-transact-sql"></a>ASYMKEYPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эта функция возвращает свойства асимметричного ключа.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
ASYMKEYPROPERTY (Key_ID , 'algorithm_desc' | 'string_sid' | 'sid')  
```  
  
## <a name="arguments"></a>Аргументы  
*Key_ID*  
Идентификатор Key_ID асимметричного ключа в базе данных. Чтобы найти значение Key_ID, если известно только имя ключа, используйте функцию ASYMKEY_ID. *Key_ID* имеет тип данных **int**.
  
**'** algorithm_desc **'**  
Указывает, что в выходных данных возвращается описание алгоритма асимметричного ключа. Доступно только для асимметричных ключей, созданных с помощью модуля расширенного управления ключами.
  
**'** string_sid **'**  
Указывает, что в выходных данных возвращается идентификатор безопасности асимметричного ключа в формате **nvarchar()** .
  
**'** sid **'**  
Указывает, что в выходных данных возвращается идентификатор безопасности асимметричного ключа в двоичном формате.
  
## <a name="return-types"></a>Типы возвращаемых данных  
**sql_variant**
  
## <a name="permissions"></a>Разрешения  
Необходимы подходящие разрешения на асимметричный ключ, а также для вызывающей стороны не должно быть запрещено разрешение VIEW на этот асимметричный ключ. Дополнительные сведения о разрешениях для асимметричных ключей см. в разделе [CREATE ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-asymmetric-key-transact-sql.md).
  
## <a name="examples"></a>Примеры  
В следующем примере возвращаются свойства асимметричного ключа с идентификатором Key_ID 256.
  
```sql
SELECT   
ASYMKEYPROPERTY(256, 'algorithm_desc') AS Algorithm,  
ASYMKEYPROPERTY(256, 'string_sid') AS String_SID,  
ASYMKEYPROPERTY(256, 'sid') AS SID ;  
GO  
```  
  
## <a name="see-also"></a>См. также раздел
[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)  
[ALTER ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)  
[DROP ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)  
[SIGNBYASYMKEY (Transact-SQL)](../../t-sql/functions/signbyasymkey-transact-sql.md)  
[VERIFYSIGNEDBYASYMKEY (Transact-SQL)](../../t-sql/functions/verifysignedbyasymkey-transact-sql.md)  
[Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
[sys.asymmetric_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-asymmetric-keys-transact-sql.md)  
[Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)  
[ASYMKEY_ID (Transact-SQL)](../../t-sql/functions/asymkey-id-transact-sql.md)  
[SYMKEYPROPERTY (Transact-SQL)](../../t-sql/functions/symkeyproperty-transact-sql.md)
  
  
