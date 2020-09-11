---
description: Типы данных ntext, text и image (Transact-SQL)
title: Типы данных ntext, text и image (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b7b067831ca56d3dc5797aa68e4810a7e9969946
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459969"
---
# <a name="ntext-text-and-image-transact-sql"></a>Типы данных ntext, text и image (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Эти типы данных фиксированной и переменной длины предназначены для хранения символьных и двоичных данных в формате Юникод и иных форматах. Данные в формате Юникод представляются символами кодировки UNICODE UCS-2.
  
>**ВАЖНО!**  Типы данных **ntext**, **text** и **image** будут исключены в следующей версии SQL Server. Следует избегать использования этих типов данных при новой разработке и запланировать изменение приложений, использующих их в настоящий момент. Вместо них следует использовать типы данных [nvarchar(max)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md), [varchar(max)](../../t-sql/data-types/char-and-varchar-transact-sql.md)и [varbinary(max)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md) .  
  
## <a name="arguments"></a>Аргументы
**ntext**  
Данные переменной длины в кодировке Юникод с максимальной длиной строки 2^30 - 1 (1 073 741 823) байт. Размер памяти в байтах вдвое превышает длину введенной строки. Синонимом **ntext** по стандарту ISO является **national text**.
  
**text**  
Данные переменной длины не в Юникоде в кодовой странице сервера и с максимальной длиной строки 2^31-1 (2 147 483 647). Если в кодовой странице сервера используются двухбайтовые символы, объем занимаемого типом пространства все равно не превышает 2 147 483 647 байт. Он может быть менее 2 147 483 647 байт — в зависимости от строки символов.
  
**image**  
Этот тип представляет двоичные данные переменной длины, включающие от 0 до 2^31 – 1 (2 147 483 647) байт.
  
## <a name="remarks"></a>Примечания  
Для работы с данными **ntext**, **text** или **image** можно использовать перечисленные ниже функции и инструкции.
  
|Функции|Операторы|  
|---|---|
|[DATALENGTH (Transact-SQL)](../../t-sql/functions/datalength-transact-sql.md)|[READTEXT (Transact-SQL)](../../t-sql/queries/readtext-transact-sql.md)|  
|[PATINDEX (Transact-SQL)](../../t-sql/functions/patindex-transact-sql.md)|[SET TEXTSIZE (Transact-SQL)](../../t-sql/statements/set-textsize-transact-sql.md)|  
|[SUBSTRING (Transact-SQL)](../../t-sql/functions/substring-transact-sql.md)|[UPDATETEXT (Transact-SQL)](../../t-sql/queries/updatetext-transact-sql.md)|  
|[TEXTPTR (Transact-SQL)](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)|[WRITETEXT (Transact-SQL)](../../t-sql/queries/writetext-transact-sql.md)|  
|[TEXTVALID (Transact-SQL)](../../t-sql/functions/text-and-image-functions-textvalid-transact-sql.md)||  
  
## <a name="see-also"></a>См. также раздел
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Преобразование типов данных (ядро СУБД)](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[LIKE (Transact-SQL)](../../t-sql/language-elements/like-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md)

