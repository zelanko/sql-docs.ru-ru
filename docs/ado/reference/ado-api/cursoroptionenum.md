---
title: Курсороптионенум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorOptionEnum
helpviewer_keywords:
- CursorOptionEnum enumeration [ADO]
ms.assetid: 4e10cda7-ce81-4466-94c2-844d38191cf1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1d5cc44950754c4b63e644d2d9210edcc94bd9ff
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67933263"
---
# <a name="cursoroptionenum"></a>CursorOptionEnum
Указывает, для каких функций должен проверяться метод [поддержки](../../../ado/reference/ado-api/supports-method.md) .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**ададднев**|0x1000400|Поддерживает метод [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) для добавления новых записей.|  
|**адаппрокспоситион**|0x4000|Поддерживает свойства [примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) и [примеры absolutepage](../../../ado/reference/ado-api/absolutepage-property-ado.md) .|  
|**адбукмарк**|0x2000|Поддерживает свойство [Bookmark](../../../ado/reference/ado-api/bookmark-property-ado.md) для получения доступа к конкретным записям.|  
|**adDelete**|0x1000800|Поддерживает метод [Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md) для удаления записей.|  
|**adFind**|0x80000|Поддерживает метод [Find](../../../ado/reference/ado-api/find-method-ado.md) для поиска строки в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md).|  
|**adHoldRecords**|0x100|Получает больше записей или изменяет следующее расположение без фиксации всех ожидающих изменений.|  
|**адиндекс**|0x100000|Поддерживает свойство [index](../../../ado/reference/ado-api/index-property.md) для именования индекса.|  
|**adMovePrevious**|0x200|Поддерживает методы [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) и [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) , а также методы [Move](../../../ado/reference/ado-api/move-method-ado.md) или [GetRows](../../../ado/reference/ado-api/getrows-method-ado.md) для перемещения текущей позиции записи назад без указания закладок.|  
|**аднотифи**|0x40000|Указывает, что базовый поставщик данных поддерживает уведомления (которые определяют, поддерживаются ли события **набора записей** ).|  
|**адресинк**|0x20000|Поддерживает метод [Resync](../../../ado/reference/ado-api/resync-method.md) для обновления курсора с данными, видимыми в базовой базе данных.|  
|**адсик**|0x200000|Поддерживает метод [Seek](../../../ado/reference/ado-api/seek-method.md) для поиска строки в **наборе записей**.|  
|**adUpdate**|0x1008000|Поддерживает метод [Update](../../../ado/reference/ado-api/update-method.md) для изменения существующих данных.|  
|**adUpdateBatch**|0x10000|Поддерживает пакетное обновление (методы[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) и [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) ) для передачи групп изменений поставщику.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|AdoEnums.CursorOption.ADDNEW|  
|Адоенумс. Курсороптион. АППРОКСПОСИТИОН|  
|Адоенумс. Курсороптион. BOOKMARK|  
|Адоенумс. Курсороптион. DELETE|  
|Адоенумс. Курсороптион. FIND|  
|Адоенумс. Курсороптион. ХОЛДРЕКОРДС|  
|Адоенумс. Курсороптион. INDEX|  
|Адоенумс. Курсороптион. MOVEPREVIOUS|  
|Адоенумс. Курсороптион. NOTIFY|  
|Адоенумс. Курсороптион. Повторная синхронизация|  
|Адоенумс. Курсороптион. SEEK|  
|Адоенумс. Курсороптион. UPDATE|  
|Адоенумс. Курсороптион. UPDATEBATCH|  
  
## <a name="applies-to"></a>Применяется к  
 [Метод Supports](../../../ado/reference/ado-api/supports-method.md)
