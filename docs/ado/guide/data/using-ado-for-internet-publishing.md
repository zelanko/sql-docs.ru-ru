---
title: Использование ADO для публикации в Интернете | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- urls [ADO]
ms.assetid: d399fce4-b70b-418f-8110-3deb3448863c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3261fc8eb910fb0b7b627b11a3bc89bb682f01bb
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273213"
---
# <a name="using-ado-for-internet-publishing"></a>Использование ADO для публикации в Интернете
[Поставщик OLE DB для публикаций в Интернете](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md) показывает конкретный пример обращения к разнородных данных с помощью ADO. Несмотря на то, что в примерах этого раздела будет характерно использование службу публикации в Интернете, принципы показано должна быть одинаковой при использовании ADO с другими поставщиками для разнородных данных, такого как поставщик хранилища электронной почты.  
  
## <a name="urls"></a>URL-адреса  
 Разрываться (URL) используется в качестве альтернативы для строки подключения и текст команды для указания источников данных и расположение файлов и каталогов. Можно использовать URL-адреса с существующим [подключения](../../../ado/reference/ado-api/connection-object-ado.md) и **записей** объектов и с **запись** и **поток** объектов.  
  
 Дополнительные сведения о том, как использовать URL-адреса см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="record-fields"></a>Поля записей  
 Отличительный признак различие между разнородными данными и однородные данные состоит в том для каждой строки данных, первое, или **запись**, может иметь разный набор столбцов, или **поля**. Однородные данные каждая строка имеет тот же набор столбцов. Дополнительные сведения о полях, относящиеся к службу публикации в Интернете см. в разделе [записи и поля дополнительных Provider-Supplied](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
### <a name="appending-new-fields"></a>Добавление новых полей  
 Несколько объектов ADO были улучшены для работы вместе с **запись** и **поток** объектов.  
  
-   [Поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции [Append](../../../ado/reference/ado-api/append-method-ado.md) метод, который создает и добавляет [поле](../../../ado/reference/ado-api/field-object.md) объект в коллекцию, можно также указать значение **поле**.  
  
-   [Обновление](../../../ado/reference/ado-api/update-method.md) завершает метод добавления и удаления полей в коллекцию.  
  
-   Как ярлык и альтернатива **Append** метод, можно создать поля путем присвоения значения полю не определено или удаленных ранее.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Поставщик OLE DB для публикации в Интернете](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)  
  
-   [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)  
  
-   [Абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md)  
  
-   [Записи и предоставляемые поставщиком поля](../../../ado/guide/data/records-and-provider-supplied-fields.md)  
  
## <a name="see-also"></a>См. также  
 [Объект записи (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Объект потока (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [Журнал объектов ADO](../../../ado/guide/ado-history.md)
