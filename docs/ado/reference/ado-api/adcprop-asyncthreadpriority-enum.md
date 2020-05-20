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
author: rothja
ms.author: jroth
ms.openlocfilehash: ecdc80a2f1e1ace36170a9b4527ba01f0b02ee11
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760660"
---
# <a name="adcprop_asyncthreadpriority_enum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
Для объекта [RECORDSET](../../../ado/reference/ado-api/recordset-object-ado.md) RDS указывает приоритет выполнения асинхронного потока, который получает данные.  
  
 Используйте эти константы с динамическим свойством " **набор записей** "**приоритета фонового потока**", которое указывается в индексе динамического свойства ADO-to-OLE DB и описано в [службе курсора Майкрософт для OLE DBной](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) документации.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**адприоритябовенормал**|4|Устанавливает приоритет между обычным и высшим.|  
|**адприоритибеловнормал**|2|Устанавливает приоритет между наименьшим и нормальным.|  
|**адприоритихигхест**|5|Устанавливает приоритет максимально возможного.|  
|**адприоритиловест**|1|Устанавливает для приоритета наименьшее возможное значение.|  
|**адприоритинормал**|3|Задает для приоритета значение Обычная.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. Адкпропасинксреадприорити. ABOVENORMAL|  
|Адоенумс. Адкпропасинксреадприорити. BELOWNORMAL|  
|Адоенумс. Адкпропасинксреадприорити. ВЫСШИй|  
|Адоенумс. Адкпропасинксреадприорити. НИЗШИй|  
|Адоенумс. Адкпропасинксреадприорити. Обычная|
