---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b1870d8cd8253e1b6de74ce093d51ca6e33c5c6d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67930937"
---
# <a name="source-property-ado-record"></a>Свойство Source (объект Record ADO)
Указывает источник данных или объект, представленный [записью](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Variant** , указывающее сущность, представленную **записью**.  
  
## <a name="remarks"></a>Remarks  
 Свойство **Source** возвращает *Исходный* аргумент метода [Open](../../../ado/reference/ado-api/open-method-ado-record.md) объекта **Record** . Он может содержать абсолютную или относительную строку URL-адреса. Абсолютный URL-адрес можно использовать без задания свойства [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) для непосредственного открытия объекта **записи** . В этом случае создается неявный объект **соединения** .  
  
 Свойство **Source** может также содержать ссылку на уже открытый **набор записей**, который открывает объект **Record** , представляющий текущую строку в **наборе записей**.  
  
 Свойство **Source** может также содержать ссылку на объект [Command](../../../ado/reference/ado-api/command-object-ado.md) , который возвращает одну строку данных от поставщика.  
  
 Если свойство **ActiveConnection** также задано, то свойство **Source** должно указывать на некоторый объект, существующий в области этого соединения. Например, в пространствах имен, структурированных в виде дерева, если свойство **Source** содержит абсолютный URL-адрес, оно должно указывать на узел, который существует внутри области узла, определяемого URL-адресом в строке подключения. Если свойство **Source** содержит относительный URL-адрес, то он проверяется в контексте, заданном свойством **ActiveConnection** .  
  
 Свойство **Source** доступно для чтения и записи, пока объект **Record** закрыт и доступен только для чтения, пока открыт объект **записи** .  
  
> [!NOTE]
>  URL-адреса, использующие схему HTTP, автоматически вызывают [поставщик OLE DB Майкрософт для публикации в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство Source (ошибка ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Свойство Source (объект Recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
