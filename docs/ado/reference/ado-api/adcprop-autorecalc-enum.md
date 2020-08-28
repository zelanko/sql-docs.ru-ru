---
description: ADCPROP_AUTORECALC_ENUM
title: ADCPROP_AUTORECALC_ENUM | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 571d3eb0d8d836a96b2f3f7a79807bd2d2c16fdf
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88976845"
---
# <a name="adcprop_autorecalc_enum"></a>ADCPROP_AUTORECALC_ENUM
Указывает, когда поставщик [мсдаташапе](../../guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) повторно вычисляет статистические и вычисляемые столбцы в иерархическом наборе записей.  
  
 Эти константы используются только с поставщиком **мсдаташапе** и динамическим свойством **"автоматическое перерасчет**" **набора записей** , на которое ссылается [индекс динамического свойства ADO](./ado-dynamic-property-index.md) и описаны в [службе курсора майкрософт для OLE DB](../../guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) или [службы формирования данных Майкрософт для OLE DB](../../guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) документации.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**адрекалкалвайс**|1|По умолчанию. Повторно вычисляется каждый раз, когда поставщик **мсдаташапе** определяет значения, от которых зависит вычисляемые столбцы.|  
|**адрекалкупфронт**|0|Вычисляет только при первоначальном построении иерархического **набора записей**.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.