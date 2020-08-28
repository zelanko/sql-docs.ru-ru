---
description: Использование ADO для публикации в Интернете
title: Использование ADO для публикации в Интернете | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 774ff9b0728d362822c72047b573ab9def944d18
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979041"
---
# <a name="using-ado-for-internet-publishing"></a>Использование ADO для публикации в Интернете
[Поставщик OLE DB для публикации в Интернете](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md) показывает конкретный пример доступа к разнородным данным с помощью ADO. Несмотря на то, что примеры в этом разделе относятся к использованию поставщика публикации в Интернете, эти принципы должны быть похожи при использовании ADO с другими поставщиками для разнородных данных, например поставщика в хранилище электронной почты.  
  
## <a name="urls"></a>URL-адреса  
 Универсальные указатели ресурсов (URL-адреса) можно использовать в качестве альтернативы строкам подключения и тексту команд для указания источников данных и расположения файлов и каталогов. Можно использовать URL-адреса с существующим [соединением](../../../ado/reference/ado-api/connection-object-ado.md) и объектами **набора записей** , а также объектами **Record** и **Stream** .  
  
 Дополнительные сведения об использовании URL-адресов см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="record-fields"></a>Поля записей  
 Различие различий между разнородными и однородными данными заключается в том, что для первого, каждой строки данных или **записи**может быть другой набор столбцов или **полей**. Для однородных данных каждая строка имеет одинаковый набор столбцов. Дополнительные сведения о полях, относящихся к поставщику публикации в Интернете, см. в разделе [записи и предоставляемые поставщиком дополнительные поля](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
### <a name="appending-new-fields"></a>Добавление новых полей  
 Несколько объектов ADO были расширены для совместной работы с объектами **Record** и **Stream** .  
  
-   Метод [append](../../../ado/reference/ado-api/append-method-ado.md) коллекции [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) , который создает и добавляет объект [field](../../../ado/reference/ado-api/field-object.md) в коллекцию, может также указывать значение **поля**.  
  
-   Метод [Update](../../../ado/reference/ado-api/update-method.md) завершает Добавление или удаление полей в коллекции.  
  
-   В качестве ярлыка и альтернативы методу **append** можно создать поля, назначив значение неопределенному или ранее удаленному полю.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Поставщик OLE DB для публикации в Интернете](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)  
  
-   [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md)  
  
-   [Абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md)  
  
-   [Записи и предоставляемые поставщиком поля](../../../ado/guide/data/records-and-provider-supplied-fields.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [Журнал объектов ADO](../../../ado/guide/ado-history.md)
