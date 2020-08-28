---
description: CursorOptionEnum
title: Курсороптионенум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a14102f57f2b328314e20e4124ca7e78258fb7e0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974355"
---
# <a name="cursoroptionenum"></a>CursorOptionEnum
Указывает, для каких функций должен проверяться метод [поддержки](./supports-method.md) .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**ададднев**|0x1000400|Поддерживает метод [AddNew](./addnew-method-ado.md) для добавления новых записей.|  
|**адаппрокспоситион**|0x4000|Поддерживает свойства [примеры AbsolutePosition](./absoluteposition-property-ado.md) и [примеры absolutepage](./absolutepage-property-ado.md) .|  
|**адбукмарк**|0x2000|Поддерживает свойство [Bookmark](./bookmark-property-ado.md) для получения доступа к конкретным записям.|  
|**adDelete**|0x1000800|Поддерживает метод [Delete](./delete-method-ado-recordset.md) для удаления записей.|  
|**adFind**|0x80000|Поддерживает метод [Find](./find-method-ado.md) для поиска строки в [наборе записей](./recordset-object-ado.md).|  
|**adHoldRecords**|0x100|Получает больше записей или изменяет следующее расположение без фиксации всех ожидающих изменений.|  
|**адиндекс**|0x100000|Поддерживает свойство [index](./index-property.md) для именования индекса.|  
|**adMovePrevious**|0x200|Поддерживает методы [MoveFirst](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md) и [MovePrevious](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md) , а также методы [Move](./move-method-ado.md) или [GetRows](./getrows-method-ado.md) для перемещения текущей позиции записи назад без указания закладок.|  
|**аднотифи**|0x40000|Указывает, что базовый поставщик данных поддерживает уведомления (которые определяют, поддерживаются ли события **набора записей** ).|  
|**адресинк**|0x20000|Поддерживает метод [Resync](./resync-method.md) для обновления курсора с данными, видимыми в базовой базе данных.|  
|**адсик**|0x200000|Поддерживает метод [Seek](./seek-method.md) для поиска строки в **наборе записей**.|  
|**adUpdate**|0x1008000|Поддерживает метод [Update](./update-method.md) для изменения существующих данных.|  
|**adUpdateBatch**|0x10000|Поддерживает пакетное обновление (методы[UpdateBatch](./updatebatch-method.md) и [CancelBatch](./cancelbatch-method-ado.md) ) для передачи групп изменений поставщику.|  
  
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
  
## <a name="applies-to"></a>Применение  
 [Метод Supports](./supports-method.md)