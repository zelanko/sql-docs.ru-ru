---
title: Метод Open (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Open
- Cellset::Open
helpviewer_keywords:
- Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 089fad427989c26ed1ed22ec3e9267297a29b820
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949387"
---
# <a name="open-method-ado-md"></a>Метод Open (многомерные объекты ADO)
Извлекает результаты многомерного запроса и возвращает результаты в набор [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *Источник*  
 Необязательный параметр. Значение **типа Variant** , результатом которого является допустимый многомерный запрос, например запрос многомерного выражения (MDX). *Исходный* аргумент соответствует свойству [Source](../../../ado/reference/ado-md-api/source-property-ado-md.md) . Дополнительные сведения о многомерных выражениях см. в OLE DB документации по [OLAP](https://msdn.microsoft.com/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3) в пакете SDK компонентов доступа к данным Microsoft.  
  
 *ActiveConnection*  
 Необязательный параметр. **Значение типа Variant** , результатом которого является строка, указывающая допустимое имя переменной объекта [подключения](../../../ado/reference/ado-api/connection-object-ado.md) ADO или определение соединения. Аргумент *ActiveConnection* задает соединение, в котором будет открыт объект набора [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) . При передаче определения соединения для этого аргумента ADO открывает новое соединение, используя указанные параметры. Аргумент *ActiveConnection* соответствует свойству [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) .  
  
## <a name="remarks"></a>Remarks  
 Метод **Open** выдает ошибку, если какой-либо из его параметров опущен, а соответствующее значение свойства не было задано до попытки открыть набор **ячеек**.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример набора ячеек (Visual Basic)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Свойство ActiveConnection (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)   
 [Метод Close (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Свойство Source (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/source-property-ado-md.md)   
 [Свойство State (многомерные объекты ADO)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
