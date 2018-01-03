---
title: "ADCPROP_AUTORECALC_ENUM | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: ADCPROP_AUTORECALC_ENUM
helpviewer_keywords: ADCPROP_AUTORECALC_ENUM [ADO]
ms.assetid: ded4f087-87b9-4efa-8026-bde53d3e9e8a
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0be561a70465aab4483fc3a2e870cbc9b68972b8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
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
