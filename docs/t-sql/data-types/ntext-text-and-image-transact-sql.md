---
title: "ntext, text и image (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ntext_TSQL
- ntext
dev_langs:
- TSQL
helpviewer_keywords:
- text data type, about text data type
- text [SQL Server], data types
- ntext data type
- ntext data type, about ntext data type
- image data type, about image data type
ms.assetid: b0d8769c-7598-4f97-8162-ace5f182b5bc
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 76b78b01596b484bc35df1a1e468c5b2bb8ece63
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="ntext-text-and-image-transact-sql"></a>Типы данных ntext, text и image (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эти типы данных фиксированной и переменной длины предназначены для хранения символьных и двоичных данных в формате Юникод и иных форматах. Данные в формате Юникод представляются символами кодировки UNICODE UCS-2.
  
>**ВАЖНО!**  **ntext**, **текст**, и **изображение** типов данных будет удалена в будущей версии SQL Server. Следует избегать использования этих типов данных при новой разработке и запланировать изменение приложений, использующих их в настоящий момент. Вместо них следует использовать типы данных [nvarchar(max)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md), [varchar(max)](../../t-sql/data-types/char-and-varchar-transact-sql.md)и [varbinary(max)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md) .  
  
  
## <a name="arguments"></a>Аргументы  
**ntext**  
Данные переменной длины в кодировке Юникод с максимальной длиной строки 2^30 - 1 (1 073 741 823) байт. Размер памяти в байтах вдвое превышает длину введенной строки. Синонимом по стандарту ISO для **ntext** — **national текст**.
  
**text**  
Данные переменной длины не в Юникоде в кодовой странице сервера и с максимальной длиной строки 2^31-1 (2 147 483 647). Если в кодовой странице сервера используются двухбайтовые символы, объем занимаемого типом пространства все равно не превышает 2 147 483 647 байт. Он может быть менее 2 147 483 647 байт — в зависимости от строки символов.
  
**image**  
Этот тип представляет двоичные данные переменной длины, включающие от 0 до 2^31 – 1 (2 147 483 647) байт.
  
## <a name="remarks"></a>Замечания  
Следующие функции и операторы можно использовать с **ntext**, **текст**, или **изображения** данные.
  
|Функции|Инструкции|  
|---|---|
|[DATALENGTH &#40; Transact-SQL &#41;](../../t-sql/functions/datalength-transact-sql.md)|[READTEXT &#40; Transact-SQL &#41;](../../t-sql/queries/readtext-transact-sql.md)|  
|[Функция PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)|[Значение TEXTSIZE &#40; Transact-SQL &#41;](../../t-sql/statements/set-textsize-transact-sql.md)|  
|[ПОДСТРОКА &#40; Transact-SQL &#41;](../../t-sql/functions/substring-transact-sql.md)|[UPDATETEXT &#40; Transact-SQL &#41;](../../t-sql/queries/updatetext-transact-sql.md)|  
|[TEXTPTR &#40; Transact-SQL &#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)|[WRITETEXT (Transact-SQL)](../../t-sql/queries/writetext-transact-sql.md)|  
|[TEXTVALID &#40; Transact-SQL &#41;](../../t-sql/functions/text-and-image-functions-textvalid-transact-sql.md)||  
  
## <a name="see-also"></a>См. также:
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Преобразование типов данных &#40; компонент Database Engine &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[КАК &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md)


