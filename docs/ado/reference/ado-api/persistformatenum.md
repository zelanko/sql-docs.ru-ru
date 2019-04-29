---
title: PersistFormatEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 851106109d195ae6f5d6f66d3944e486d58504c1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63027837"
---
# <a name="persistformatenum"></a>PersistFormatEnum
Указывает формат, в котором следует сохранить [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Указывает формат TableGram дополнительные данные (ADTG).|  
|**adPersistADO**|1|Указывает, что будет использоваться ADO собственный формат расширяемого языка разметки (XML). Это значение совпадает со значением adPersistXML и включен для обеспечения обратной совместимости.|  
|**adPersistXML**|1|Указывает формат расширяемого языка разметки (XML).|  
|**adPersistProviderSpecific**|2|Указывает, что поставщик будет сохраняться **записей** используя свой собственный формат.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Save](../../../ado/reference/ado-api/save-method.md)
