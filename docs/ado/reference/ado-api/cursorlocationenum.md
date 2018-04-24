---
title: CursorLocationEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorLocationEnum
helpviewer_keywords:
- CursorLocationEnum enumeration [ADO]
ms.assetid: acb255ff-1734-4b70-89bb-aef862b4c63b
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2e5dc3fa4f78881502f846e828484ea03329d91e
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="cursorlocationenum"></a>CursorLocationEnum
Указывает расположение службы курсора.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adUseClient**|3|Использует клиентские курсоры, предоставленный библиотекой локальный курсор. Службы локального курсора часто разрешает множество функций, не разрешается-драйвер курсоры и использование этого параметра может привести к дополнительным преимуществом по отношению к функции, которые будут включены. Для обеспечения обратной совместимости, синоним **adUseClientBatch** также поддерживается.|  
|**adUseNone**|1|Не использует службы курсора. (Эта константа является устаревшим и отображается только для обратной совместимости).|  
|**adUseServer**|2|По умолчанию. Использует курсоры, предоставляемые поставщиком данных или драйвера. Эти курсоры иногда являются достаточно гибкими и допускает дополнительных учета изменений, которые другим пользователям вносить в источник данных. Тем не менее некоторые возможности [служба Microsoft курсора для OLE DB](../../../ado/guide/data/the-microsoft-cursor-service-for-ole-db.md), такие как отменить связь<br /><br /> [Набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекты, нельзя имитировать только с курсорами на стороне сервера, и эти функции будут недоступны, если этот параметр.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.CursorLocation.CLIENT|  
|AdoEnums.CursorLocation.NONE|  
|AdoEnums.CursorLocation.SERVER|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство CursorLocation (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)
