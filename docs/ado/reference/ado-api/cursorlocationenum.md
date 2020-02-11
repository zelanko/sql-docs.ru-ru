---
title: Курсорлокатионенум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorLocationEnum
helpviewer_keywords:
- CursorLocationEnum enumeration [ADO]
ms.assetid: acb255ff-1734-4b70-89bb-aef862b4c63b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b3af18120af91fe06da48c2e3636bf8a7c572161
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919294"
---
# <a name="cursorlocationenum"></a>CursorLocationEnum
Указывает расположение службы курсора.  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адусеклиент**|3|Использует курсоры на стороне клиента, предоставляемые локальной библиотекой курсоров. Службы локальных курсоров часто допускают множество функций, которые предоставленные драйвером курсоры не могут, поэтому использование этого параметра может обеспечить преимущество в отношении функций, которые будут включены. Для обеспечения обратной совместимости также поддерживается **адусеклиентбатч** синонимов.|  
|**адусеноне**|1|Не использует службы курсоров. (Эта константа устарела и отображается исключительно в целях обратной совместимости.)|  
|**адусесервер**|2|По умолчанию. Использует курсоры, предоставляемые поставщиком данных или драйвером. Эти курсоры иногда являются очень гибкими и обеспечивают дополнительную чувствительность к изменениям, внесенным другими пользователями в источник данных. Однако некоторые функции [службы курсора Майкрософт для OLE DB](../../../ado/guide/data/the-microsoft-cursor-service-for-ole-db.md), например, не связаны<br /><br /> Объекты [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) не могут быть смоделированы с помощью курсоров на стороне сервера, и эти функции будут недоступны при использовании этого параметра.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|Адоенумс. CursorLocation. CLIENT|  
|Адоенумс. CursorLocation. NONE|  
|Адоенумс. CursorLocation. SERVER|  
  
## <a name="applies-to"></a>Применяется к  
 [Свойство CursorLocation (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)
