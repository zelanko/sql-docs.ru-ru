---
description: Поставщик сохраняемости Microsoft OLE DB (поставщик служб ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 9a1211a84bf42afdb406c085e57f5bb36f48a168
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454116"
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

|Константа|Описание|
|--------------|-----------------|
|E_BADSTREAM|Открытый файл имеет недопустимый формат (то есть формат не АДТГ или XML).|
|E_CANTPERSISTROWSET|Сохраненный объект **набора записей** имеет характеристики, которые не позволяют сохранить его.|

## <a name="remarks"></a>Комментарии
 Поставщик сохраняемости Microsoft OLE DB не предоставляет динамические свойства.

 В настоящее время невозможно сохранить только параметризованные иерархические объекты **Recordset** .

 Дополнительные сведения о постоянном хранении объектов **набора записей** см. в разделе [Сохранение набора записей](../../../ado/guide/data/more-about-recordset-persistence.md).

 Если для открытия **набора записей** используется поток, не должны быть заданы параметры, отличные от *исходного* параметра метода **Open** .

## <a name="see-also"></a>См. также
[Поставщик сохраняемости Microsoft OLE DB (поставщик служб ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)
