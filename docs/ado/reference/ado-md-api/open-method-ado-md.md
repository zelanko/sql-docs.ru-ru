---
description: Метод Open (многомерные объекты ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6a7a0074df9713c49c9d334b2e7e92b129f56594
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777943"
---
# <a name="open-method-ado-md"></a>Метод Open (многомерные объекты ADO)
Извлекает результаты многомерного запроса и возвращает результаты в набор [ячеек](./cellset-object-ado-md.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательный элемент. Значение **типа Variant** , результатом которого является допустимый многомерный запрос, например запрос многомерного выражения (MDX). *Исходный* аргумент соответствует свойству [Source](./source-property-ado-md.md) . Дополнительные сведения о многомерных выражениях см. в OLE DB документации по [OLAP](/previous-versions/windows/desktop/ms717005(v=vs.85)) в пакете SDK компонентов доступа к данным Microsoft.  
  
 *ActiveConnection*  
 Необязательный элемент. **Значение типа Variant** , результатом которого является строка, указывающая допустимое имя переменной объекта [подключения](../ado-api/connection-object-ado.md) ADO или определение соединения. Аргумент *ActiveConnection* задает соединение, в котором будет открыт объект набора [ячеек](./cellset-object-ado-md.md) . При передаче определения соединения для этого аргумента ADO открывает новое соединение, используя указанные параметры. Аргумент *ActiveConnection* соответствует свойству [ActiveConnection](./activeconnection-property-ado-md.md) .  
  
## <a name="remarks"></a>Remarks  
 Метод **Open** выдает ошибку, если какой-либо из его параметров опущен, а соответствующее значение свойства не было задано до попытки открыть набор **ячеек**.  
  
## <a name="applies-to"></a>Применение  
 [Объект Cellset (многомерные объекты ADO)](./cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Пример набора ячеек (Visual Basic)](./cellset-example-vb.md)   
 [Свойство ActiveConnection (объекты данных ActiveX (MD))](./activeconnection-property-ado-md.md)   
 [Метод Close (объекты данных ActiveX (MD))](./close-method-ado-md.md)   
 [Объект Connection (ADO)](../ado-api/connection-object-ado.md)   
 [Свойство Source (объекты данных ActiveX (MD))](./source-property-ado-md.md)   
 [Свойство State (многомерные объекты ADO)](./state-property-ado-md.md)