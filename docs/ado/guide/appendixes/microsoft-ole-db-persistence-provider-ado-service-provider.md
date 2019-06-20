---
title: Поставщик сохраняемости Microsoft OLE DB (ADO поставщиком услуг) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB persistence provider
- persistence provider [ADO]
- OLE DB persistence provider [ADO]
ms.assetid: e75ef0dc-2016-4fcc-8918-23311c0d4e02
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d1ae4f8cba9235700edf410904862d39ed4f7f64
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702995"
---
# <a name="microsoft-ole-db-persistence-provider-overview"></a>Общие сведения о поставщике Microsoft OLE DB сохраняемости
Поставщик сохраняемости Microsoft OLE DB позволяет сохранить [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта в файл и последующее восстановление, **записей** объекта из файла. Сведения о схеме, данных, а отложенные изменения сохраняются.

 Вы можете сохранить **записей** в собственный формат дополнительные данные таблицы Gram (ADTG) или формате open Extensible Markup Language (XML).

## <a name="provider-keyword"></a>Ключевое слово службы
 Чтобы вызвать этот поставщик, укажите следующие слова и значение в строке подключения.

```vb
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
