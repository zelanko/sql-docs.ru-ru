---
title: IsolationLevelEnum | Документы Microsoft
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
- IsolationLevelEnum
helpviewer_keywords:
- IsolationLevelEnum enumeration [ADO]
ms.assetid: 8e17a7bc-b8a3-4ae2-b6c9-ce088ad31fdf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b7f159568be94e20260809e05d2234e0274e29c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="isolationlevelenum"></a>IsolationLevelEnum
Задает уровень изоляции транзакции для [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adXactUnspecified**|-1|Указывает, что поставщик с использованием другой уровень изоляции не указан, но не удается определить уровень.|  
|**adXactChaos**|16|Указывает, что ожидающие изменения более изолированных транзакций не может быть перезаписан.|  
|**adXactBrowse**|256|Указывает, что в одной транзакции можно просмотреть незафиксированные изменения в других транзакциях.|  
|**adXactReadUncommitted**|256|То же, что **adXactBrowse**.|  
|**adXactCursorStability**|4096|Указывает, что из одной операции можно просмотреть изменения в других транзакциях только после их фиксации.|  
|**adXactReadCommitted**|4096|То же, что **adXactCursorStability**.|  
|**adXactRepeatableRead**|65536|Указывает, что из одной транзакции нельзя увидеть изменения, сделанные в других транзакциях, но выполнение обновления наборов, можно получить новые **записей** объектов.|  
|**adXactIsolated**|1048576|Указывает, что транзакции выполняются отдельно от других транзакций.|  
|**adXactSerializable**|1048576|То же, что **adXactIsolated**.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.IsolationLevel.UNSPECIFIED|  
|AdoEnums.IsolationLevel.CHAOS|  
|AdoEnums.IsolationLevel.BROWSE|  
|AdoEnums.IsolationLevel.READUNCOMMITTED|  
|AdoEnums.IsolationLevel.CURSORSTABILITY|  
|AdoEnums.IsolationLevel.READCOMMITTED|  
|AdoEnums.IsolationLevel.REPEATABLEREAD|  
|AdoEnums.IsolationLevel.ISOLATED|  
|AdoEnums.IsolationLevel.SERIALIZABLE|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md)
