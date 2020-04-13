---
title: Пример. Получение двоичных данных | Документация Майкрософт
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
ms.openlocfilehash: 8d66e1ec9c580030f1f65f030cdb0367d8f4f430
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664506"
---
# <a name="example-retrieving-binary-data"></a>Пример. Получение двоичных данных

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

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
