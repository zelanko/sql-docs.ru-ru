---
title: MoveRecordOptionsEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- MoveRecordOptionsEnum
helpviewer_keywords:
- MoveRecordOptionsEnum enumeration [ADO]
ms.assetid: f53c2ce4-1021-4a45-92b8-775e8bebad99
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb86b01a42a097210801fd3654ff2af80df24e39
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47701593"
---
# <a name="moverecordoptionsenum"></a>MoveRecordOptionsEnum
Задает поведение [записи](../../../ado/reference/ado-api/record-object-ado.md) объект [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) метод.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adMoveUnspecified**|-1|По умолчанию. Выполняет операцию перемещения по умолчанию: операция завершается ошибкой, если целевой файл или каталог уже существует, и операция обновляет гипертекстовых ссылок.|  
|**adMoveOverWrite**|1|Перезаписывает конечный файл или каталог, даже если он уже существует.|  
|**adMoveDontUpdateLinks**|2|Изменяет поведение по умолчанию **MoveRecord** метод, не обновляя гипертекстовых ссылок источника **записи**. Поведение по умолчанию зависит от возможностей поставщика. Операции перемещения обновляет ссылки, если поставщик может быть перенесен. Если поставщик не может исправить ссылки или если это значение не указано, перемещение успешно, даже если ссылки не были исправлены.|  
|**adMoveAllowEmulation**|4|Запросы, что поставщик попытка моделировать перемещения (с помощью загрузки, отправка и операции удаления). Если попытка переместить **записи** завершается сбоем, так как URL-адрес назначения находится на другом сервере или обслуживаемых другого поставщика, чем исходный, это может привести к повышенной задержки и потери данных, из-за возможности другого поставщика при Перемещение ресурсов между поставщиками.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Эти константы не имеют эквивалентов ADO и WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
