---
title: ADCPROP_ASYNCTHREADPRIORITY_ENUM | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM
helpviewer_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM [ADO]
ms.assetid: f0965617-17d8-41e0-98d0-f824274735a6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 22a8cd4bb8d1bdddbaaa68e92349d9c728557ac0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921465"
---
# <a name="adcprop_asyncthreadpriority_enum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
Для объекта [RECORDSET](../../../ado/reference/ado-api/recordset-object-ado.md) RDS указывает приоритет выполнения асинхронного потока, который получает данные.  
  
 Используйте эти константы с динамическим свойством " **набор записей** "**приоритета фонового потока**", которое указывается в индексе динамического свойства ADO-to-OLE DB и описано в [службе курсора Майкрософт для OLE DBной](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) документации.  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адприоритябовенормал**|4|Устанавливает приоритет между обычным и высшим.|  
|**адприоритибеловнормал**|2|Устанавливает приоритет между наименьшим и нормальным.|  
|**адприоритихигхест**|5|Устанавливает приоритет максимально возможного.|  
|**адприоритиловест**|1|Устанавливает для приоритета наименьшее возможное значение.|  
|**адприоритинормал**|3|Задает для приоритета значение Обычная.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|Адоенумс. Адкпропасинксреадприорити. ABOVENORMAL|  
|Адоенумс. Адкпропасинксреадприорити. BELOWNORMAL|  
|Адоенумс. Адкпропасинксреадприорити. ВЫСШИй|  
|Адоенумс. Адкпропасинксреадприорити. НИЗШИй|  
|Адоенумс. Адкпропасинксреадприорити. Обычная|
