---
title: Свойство (объект Record ADO) источника | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 4b053fdeae5016d7a1b489133b3a26067da7eab2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47803052"
---
# <a name="source-property-ado-record"></a>Свойство Source (объект Record ADO)
Указывает источник данных или объекта, представленного [записи](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **Variant** значение, указывающее сущности, представленной **записи**.  
  
## <a name="remarks"></a>Примечания  
 **Источника** возвращает *источника* аргумент **записи** объект [откройте](../../../ado/reference/ado-api/open-method-ado-record.md) метод. Оно может содержать строку абсолютный или относительный URL-адрес. Абсолютный URL-адрес можно использовать без параметра [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойства, чтобы напрямую открыть **записи** объекта. Неявный **подключения** в этом случае создается объект.  
  
 **Источника** свойство также может содержать ссылку на уже открытого **записей**, чтобы открыть **записи** объект, представляющий текущую строку в  **Набор записей**.  
  
 **Источника** свойство также может содержать ссылку на [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта, который возвращает одну строку данных от поставщика.  
  
 Если **ActiveConnection** задается, а затем **источника** свойство должно указывать некоторый объект, который существует в пределах данного соединения. Например, в древовидной пространства имен Если **источника** свойство содержит абсолютный URL-адрес, он должен указывать на узел, который существует в области узла, идентифицируемого выражением URL-адреса в строке подключения. Если **источника** свойство содержит относительный URL-адрес, а затем для проверки в контексте задается **ActiveConnection** свойство.  
  
 **Источника** свойство доступно для чтения/записи при **записи** объект закрывается и только для чтения при **записи** открыт.  
  
> [!NOTE]
>  URL-адреса, с использованием схемы http, автоматически вызывает метод [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Source (объект Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Свойство Source (объект Recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
