---
title: Использование ADO для публикации в Интернете | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- urls [ADO]
ms.assetid: d399fce4-b70b-418f-8110-3deb3448863c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d779204046b9bca2591fbdc9459d7c6b53061ff4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63184965"
---
# <a name="using-ado-for-internet-publishing"></a>Использование ADO для публикации в Интернете
[Поставщик OLE DB для публикаций в Интернете](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md) показано содержится конкретный пример, доступ к разнородных данных с помощью ADO. Несмотря на то, что в примерах этого раздела будет специально для использования поставщика Интернет-публикаций, демонстрируются принципы должен выглядеть при использовании ADO с другими поставщиками для разнородных данных, таких как поставщик в хранилище по электронной почте.  
  
## <a name="urls"></a>URL-адреса  
 Унифицированные указатели ресурсов (URL-адреса) можно использовать в качестве альтернативы для строки подключения и текст команды для указания источников данных и расположение файлов и каталогов. URL-адреса можно использовать с существующим [подключения](../../../ado/reference/ado-api/connection-object-ado.md) и **записей** объектов и с **записи** и **Stream** объектов.  
  
 Дополнительные сведения о том, как использовать URL-адреса см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="record-fields"></a>Запись поля  
 Отличительный признак разницу между разнородными данными и однородных данных применяется для предыдущий, каждая строка данных, или **записи**, может иметь другой набор столбцов, или **поля**. Для однородной данных каждая строка содержит тот же набор столбцов. Дополнительные сведения о поля, присущие службу публикации в Интернете, см. в разделе [записи и поля дополнительных Provider-Supplied](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
### <a name="appending-new-fields"></a>Добавление нового поля  
 Несколько объектов ADO были улучшены для работы совместно с **записи** и **Stream** объектов.  
  
-   [Поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции [Append](../../../ado/reference/ado-api/append-method-ado.md) метод, который создает и добавляет [поле](../../../ado/reference/ado-api/field-object.md) объекта в коллекцию, можно также указать значение **поле**.  
  
-   [Обновления](../../../ado/reference/ado-api/update-method.md) завершает метод добавления или удаления полей в коллекцию.  
  
-   Как ярлык и альтернативой **Append** метода, поля можно создать путем присвоения значения полю неопределенный или удаленная.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Поставщик OLE DB для публикации в Интернете](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)  
  
-   [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)  
  
-   [Абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md)  
  
-   [Записи и предоставляемые поставщиком поля](../../../ado/guide/data/records-and-provider-supplied-fields.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [Журнал объектов ADO](../../../ado/guide/ado-history.md)
