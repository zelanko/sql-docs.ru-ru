---
title: "ADCPROP_AUTORECALC_ENUM | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADCPROP_AUTORECALC_ENUM
helpviewer_keywords:
- ADCPROP_AUTORECALC_ENUM [ADO]
ms.assetid: ded4f087-87b9-4efa-8026-bde53d3e9e8a
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f5639a1e86ce6b9e46b3583c8e092e389dfa422e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="adcpropautorecalcenum"></a>ADCPROP_AUTORECALC_ENUM
Указывает, когда [MSDataShape](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) поставщик повторно вычисляет статистические и вычисляемые столбцы в иерархических записей.  
  
 Эти константы используются только с **MSDataShape** поставщика и **набора записей** »**автоматического пересчета**«динамические свойства, на которую ссылается [ADO Динамические свойства индекса](../../../ado/reference/ado-api/ado-dynamic-property-index.md) документированные в [службы курсора для OLE DB Microsoft](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) или [службы Microsoft Data Shaping Service для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) документации.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adRecalcAlways**|1|По умолчанию. Повторно вычисляет каждый раз, когда **MSDataShape** поставщик определяет значения, которые зависят от вычисляемых столбцов были изменены.|  
|**adRecalcUpFront**|0|Вычисляет только в том случае, если изначально построение иерархическое **записей**.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.
