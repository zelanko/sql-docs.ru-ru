---
title: PersistFormatEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9aa6ce5a4341c85f7763d407b0d39599b24d9441
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280613"
---
# <a name="persistformatenum"></a>PersistFormatEnum
Указывает формат, в котором следует сохранить [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Указывает формат TableGram дополнительные данные (ADTG).|  
|**adPersistADO**|1|Указывает, что будет использоваться ADO собственные формате расширяемого языка разметки (XML). Это значение совпадает со значением adPersistXML и включен для обеспечения обратной совместимости.|  
|**adPersistXML**|1|Указывает в формате расширяемого языка разметки (XML).|  
|**adPersistProviderSpecific**|2|Указывает, что поставщик будет сохраняться **записей** с использованием собственного формата.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Save](../../../ado/reference/ado-api/save-method.md)
