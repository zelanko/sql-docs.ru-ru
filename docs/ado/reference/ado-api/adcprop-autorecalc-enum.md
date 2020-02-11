---
title: ADCPROP_AUTORECALC_ENUM | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_AUTORECALC_ENUM
helpviewer_keywords:
- ADCPROP_AUTORECALC_ENUM [ADO]
ms.assetid: ded4f087-87b9-4efa-8026-bde53d3e9e8a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 738f4cece8cf2355c12c0de4ac42314152c6370a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921445"
---
# <a name="adcprop_autorecalc_enum"></a>ADCPROP_AUTORECALC_ENUM
Указывает, когда поставщик [мсдаташапе](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) повторно вычисляет статистические и вычисляемые столбцы в иерархическом наборе записей.  
  
 Эти константы используются только с поставщиком **мсдаташапе** и динамическим свойством **"автоматическое перерасчет**" **набора записей** , на которое ссылается [индекс динамического свойства ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) и описаны в [службе курсора майкрософт для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) или [службы формирования данных Майкрософт для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) документации.  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адрекалкалвайс**|1|По умолчанию. Повторно вычисляется каждый раз, когда поставщик **мсдаташапе** определяет значения, от которых зависит вычисляемые столбцы.|  
|**адрекалкупфронт**|0|Вычисляет только при первоначальном построении иерархического **набора записей**.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.
