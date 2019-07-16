---
title: IsolationLevelEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- IsolationLevelEnum
helpviewer_keywords:
- IsolationLevelEnum enumeration [ADO]
ms.assetid: 8e17a7bc-b8a3-4ae2-b6c9-ce088ad31fdf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 15ae2aac2851c496b6cac9e47d37fe5fa26b8e34
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918376"
---
# <a name="isolationlevelenum"></a>IsolationLevelEnum
Указывает уровень изоляции транзакции для [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adXactUnspecified**|-1|Указывает, что поставщик использует другой уровень изоляции, чем указано, но не удается определить уровень.|  
|**adXactChaos**|16|Указывает, что ожидающие изменения более изолированных транзакций не могут быть перезаписаны.|  
|**adXactBrowse**|256|Указывает, что в одной транзакции можно просмотреть незафиксированные изменения в других транзакциях.|  
|**значения adXactReadUncommitted**|256|Совпадение с кодом **adXactBrowse**.|  
|**adXactCursorStability**|4096|Указывает, что из одной транзакции можно просмотреть изменения в других транзакциях только после их фиксации.|  
|**adXactReadCommitted**|4096|Совпадение с кодом **adXactCursorStability**.|  
|**adXactRepeatableRead**|65536|Указывает, что из одной транзакции нельзя увидеть изменения, сделанные в других транзакциях, но выполнение обновления наборов, можно получить новые **записей** объектов.|  
|**adXactIsolated**|1048576|Указывает, что транзакции выполняются отдельно от других транзакций.|  
|**adXactSerializable**|1048576|Совпадение с кодом **adXactIsolated**.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
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
