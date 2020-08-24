---
description: Свойство Source (объект Record ADO)
title: Свойство Source (запись ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::Source
- _Record::PutRefSource
- _Record::GetSource
- _Record::put_Source
- _Record::putref_Source
- _Record::get_Source
helpviewer_keywords:
- Source property [ADO Record]
ms.assetid: 2c18279e-6f35-4af0-b12e-8f1543d9ed20
author: rothja
ms.author: jroth
ms.openlocfilehash: 0e755fb4a34e170efea760428021b540a182156c
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777413"
---
# <a name="source-property-ado-record"></a>Свойство Source (объект Record ADO)
Указывает источник данных или объект, представленный [записью](./record-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Variant** , указывающее сущность, представленную **записью**.  
  
## <a name="remarks"></a>Remarks  
 Свойство **Source** возвращает *Исходный* аргумент метода [Open](./open-method-ado-record.md) объекта **Record** . Он может содержать абсолютную или относительную строку URL-адреса. Абсолютный URL-адрес можно использовать без задания свойства [ActiveConnection](./activeconnection-property-ado.md) для непосредственного открытия объекта **записи** . В этом случае создается неявный объект **соединения** .  
  
 Свойство **Source** может также содержать ссылку на уже открытый **набор записей**, который открывает объект **Record** , представляющий текущую строку в **наборе записей**.  
  
 Свойство **Source** может также содержать ссылку на объект [Command](./command-object-ado.md) , который возвращает одну строку данных от поставщика.  
  
 Если свойство **ActiveConnection** также задано, то свойство **Source** должно указывать на некоторый объект, существующий в области этого соединения. Например, в пространствах имен, структурированных в виде дерева, если свойство **Source** содержит абсолютный URL-адрес, оно должно указывать на узел, который существует внутри области узла, определяемого URL-адресом в строке подключения. Если свойство **Source** содержит относительный URL-адрес, то он проверяется в контексте, заданном свойством **ActiveConnection** .  
  
 Свойство **Source** доступно для чтения и записи, пока объект **Record** закрыт и доступен только для чтения, пока открыт объект **записи** .  
  
> [!NOTE]
>  URL-адреса, использующие схему HTTP, автоматически вызывают [поставщик OLE DB Майкрософт для публикации в Интернете](../../guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Применение  
 [Объект Record (ADO)](./record-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Source (ошибка ADO)](./source-property-ado-error.md)   
 [Свойство Source (объект Recordset ADO)](./source-property-ado-recordset.md)