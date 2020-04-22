---
title: Использование параметра BINARY BASE64 | Документация Майкрософт
description: Узнайте, как использовать параметр BINARY BASE64 в SQL-запросе для возвращения двоичных данных в формате кодировки Base64.
ms.custom: ''
ms.date: 04/03/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, BINARY BASE64 option
ms.assetid: 86a7bb85-7f83-412a-b775-d2c379702fe9
author: RothJa
ms.author: jroth
ms.openlocfilehash: fffd3833256ee6afa9dd3731d5cf02e99913e565
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388356"
---
# <a name="use-the-binary-base64-option"></a>Использование параметра BINARY BASE64

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Если в запросе задан аргумент BINARY BASE64, двоичные данные возвращаются в формате кодирования base64.

По умолчанию, если аргумент BINARY BASE64 не задан в запросе, режим AUTO поддерживает кодирование URL-адресов двоичных данных. Возвращается ссылка на относительный URL-адрес виртуального корня базы данных. Эта ссылка указывает на базу данных, в которой был выполнен запрос. Возвращаемую ссылку можно использовать для доступа к действительным двоичным данным в последующих операциях. Этот доступ достигается с помощью запроса SQLXML ISAPI dbobject. Для идентификации изображения запрос должен предоставить достаточно данных. Такие сведения могут включать столбцы первичного ключа.

## <a name="column-alias"></a>Псевдоним столбца

Не используйте псевдоним для двоичного столбца при запросе представления и использовании режима FOR XML AUTO. Если используется псевдоним, он возвращается в кодировке URL-адреса двоичных данных. В последующих операциях псевдоним не имеет смысла. Его и URL-адрес невозможно будет использовать для получения изображения.

### <a name="cast-to-a-blob"></a>Приведение к большому двоичному объекту

В запросе SELECT приведение любого столбца к большому двоичному объекту (BLOB) делает столбец временной сущностью. Будучи временным, BLOB-объект теряет связанное имя таблицы и имя столбца. Поэтому запросы в режиме AUTO будут формировать ошибки, так как система не будет знать, куда поместить этот объект в иерархии XML.

Например, рассмотрим следующую таблицу с одной строкой.

```sql
CREATE TABLE MyTable (Col1 int PRIMARY KEY, Col2 binary)
INSERT INTO MyTable VALUES (1, 0x7);
```

Следующий запрос вернет ошибку из-за приведения к типу BLOB:

```sql
SELECT Col1,
CAST(Col2 as image) as Col2
FROM MyTable
FOR XML AUTO;
```

Решение этой проблемы заключается в добавлении параметра BINARY BASE64 к предложению FOR XML. Если удалить приведение типов, запрос вернет нормальный результат:

```sql
SELECT Col1,
CAST(Col2 as image) as Col2
FROM MyTable
FOR XML AUTO, BINARY BASE64;
```

Предполагался следующий результат:

```console
<MyTable Col1="1" Col2="Bw==" />
```

## <a name="see-also"></a>См. также:

[Использование AUTO Mode с FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md)
