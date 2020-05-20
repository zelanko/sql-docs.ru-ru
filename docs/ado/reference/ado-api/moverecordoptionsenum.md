---
title: Моверекордоптионсенум | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 849f3720d831c17b6b9d6d2829ae0b28f19992de
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762445"
---
# <a name="moverecordoptionsenum"></a>MoveRecordOptionsEnum
Задает поведение метода [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) объекта [записи](../../../ado/reference/ado-api/record-object-ado.md) .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adMoveUnspecified**|-1|По умолчанию. Выполняет операцию перемещения по умолчанию: операция завершается ошибкой, если целевой файл или каталог уже существует, а операция обновляет гипертекстовые ссылки.|  
|**adMoveOverWrite**|1|Перезаписывает целевой файл или каталог, даже если он уже существует.|  
|**adMoveDontUpdateLinks**|2|Изменяет поведение метода **MoveRecord** по умолчанию, не обновляя гипертекстовые ссылки исходной **записи**. Поведение по умолчанию зависит от возможностей поставщика. Операция перемещения обновляет ссылки, если поставщик поддерживается. Если поставщик не может исправить ссылки или это значение не указано, перемещение проходит успешно, даже если ссылки не были исправлены.|  
|**adMoveAllowEmulation**|4|Запрашивает, что поставщик пытается имитировать перемещение (с помощью операций скачивания, отправки и удаления). Если попытка перемещения **записи** завершается ошибкой, так как URL-адрес назначения находится на другом сервере или обслуживается другим поставщиком, отличным от поставщика источника, это может привести к увеличению задержки или потере данных из-за различных возможностей поставщика при перемещении ресурсов между поставщиками.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применяется к  
 [Метод MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
