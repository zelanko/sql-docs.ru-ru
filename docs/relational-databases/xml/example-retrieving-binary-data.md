---
title: Пример Получение двоичных данных | Документация Майкрософт
description: Просмотрите пример SQL-запроса, который получает двоичные данные, используя параметры RAW и BINARY BASE64 с предложением FOR XML.
ms.custom: ''
ms.date: 04/03/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
author: RothJa
ms.author: jroth
ms.openlocfilehash: 08010e294b1b143c941774912d661a53c021a6ab
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85632790"
---
# <a name="example-retrieving-binary-data"></a>Пример Получение двоичных данных

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

В следующем запросе возвращается фотография продукта, хранящаяся в столбце с типом данных **varbinary(max)** . Для возвращения двоичных данных в base64-кодированном формате для запроса должен быть определен параметр `BINARY BASE64` .

## <a name="example"></a>Пример

```sql
USE AdventureWorks2012;
GO
SELECT ProductPhotoID, ThumbNailPhoto
FROM Production.ProductPhoto
WHERE ProductPhotoID=1
FOR XML RAW, BINARY BASE64 ;
GO
```

Предполагался следующий результат:

```console
<row ProductModelID="1" ThumbNailPhoto="base64 encoded binary data"/>
```

## <a name="see-also"></a>См. также:

[Использование RAW Mode с FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)
