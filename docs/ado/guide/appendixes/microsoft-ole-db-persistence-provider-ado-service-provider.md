---
title: Поставщик сохраняемости Microsoft OLE DB (ADO поставщиком услуг) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB persistence provider
- persistence provider [ADO]
- OLE DB persistence provider [ADO]
ms.assetid: e75ef0dc-2016-4fcc-8918-23311c0d4e02
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b7ffeec1ca14aa57876ea14cbfdb536d9207c1f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47630782"
---
# <a name="microsoft-ole-db-persistence-provider-overview"></a>Общие сведения о поставщике Microsoft OLE DB сохраняемости
Поставщик сохраняемости Microsoft OLE DB позволяет сохранить [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта в файл и последующее восстановление, **записей** объекта из файла. Сведения о схеме, данных, а отложенные изменения сохраняются.

 Вы можете сохранить **записей** в собственный формат дополнительные данные таблицы Gram (ADTG) или формате open Extensible Markup Language (XML).

## <a name="provider-keyword"></a>Ключевое слово службы
 Чтобы вызвать этот поставщик, укажите следующие слова и значение в строке подключения.

```
"Provider=MSPersist"
```

## <a name="errors"></a>ошибки
 В приложении могут быть обнаружены следующие ошибки, выданные этим поставщиком.

|Константа|Описание|
|--------------|-----------------|
|E_BADSTREAM|Файл, открытый не имеет допустимый формат (то есть, формат не ADTG или XML).|
|E_CANTPERSISTROWSET|**Записей** сохранен объект имеет характеристики, которые не допустить сохранения.|

## <a name="remarks"></a>Примечания
 Поставщик сохраняемости OLE DB Microsoft предоставляет нет динамических свойств.

 В настоящее время только параметризованные иерархические **записей** невозможно сохранить объекты.

 Дополнительные сведения о хранении постоянно **записей** объектов, см. в разделе [сохраняемости набора записей](../../../ado/guide/data/more-about-recordset-persistence.md).

 Когда поток используется для открытия **набор записей,** должна существовать без указания отличные от параметров *источника* параметр **откройте** метод.

## <a name="see-also"></a>См. также
[Поставщик Microsoft OLE DB сохраняемости (поставщик услуг ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)
