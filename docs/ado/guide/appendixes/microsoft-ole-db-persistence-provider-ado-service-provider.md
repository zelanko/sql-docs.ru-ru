---
title: Поставщик сохраняемости Microsoft OLE DB (поставщик служб ADO) | Документация Майкрософт
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
ms.openlocfilehash: 2bd341a3af2d1fdb076312b4c0993184fb4fae39
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926769"
---
# <a name="microsoft-ole-db-persistence-provider-overview"></a>Общие сведения о поставщике сохраняемости Microsoft OLE DB
Поставщик сохраняемости Microsoft OLE DB позволяет сохранить объект [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) в файл, а затем восстановить этот объект **набора записей** из файла. Сведения о схеме, данные и ожидающие изменения сохраняются.

 **Набор записей** можно сохранить в формате собственного расширенной таблицы данных (адтг) или в формате Open язык XML (XML).

## <a name="provider-keyword"></a>Ключевое слово Provider
 Чтобы вызвать этот поставщик, укажите в строке подключения следующее ключевое слово и значение.

```vb
"Provider=MSPersist"
```

## <a name="errors"></a>ошибки
 Следующие ошибки, выданные поставщиком, могут быть обнаружены в приложении.

|Постоянно|Description|
|--------------|-----------------|
|E_BADSTREAM|Открытый файл имеет недопустимый формат (то есть формат не АДТГ или XML).|
|E_CANTPERSISTROWSET|Сохраненный объект **набора записей** имеет характеристики, которые не позволяют сохранить его.|

## <a name="remarks"></a>Remarks
 Поставщик сохраняемости Microsoft OLE DB не предоставляет динамические свойства.

 В настоящее время невозможно сохранить только параметризованные иерархические объекты **Recordset** .

 Дополнительные сведения о постоянном хранении объектов **набора записей** см. в разделе [Сохранение набора записей](../../../ado/guide/data/more-about-recordset-persistence.md).

 Если для открытия **набора записей** используется поток, не должны быть заданы параметры, отличные от *исходного* параметра метода **Open** .

## <a name="see-also"></a>См. также:
[Поставщик сохраняемости Microsoft OLE DB (поставщик служб ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)
