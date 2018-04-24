---
title: CopyRecordOptionsEnum | Документы Microsoft
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
- CopyRecordOptionsEnum
helpviewer_keywords:
- CopyRecordOptionsEnum enumeration [ADO]
ms.assetid: 2fa4eec5-d50b-4fd3-8ae7-40af441ba12b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d5a571e4c68ccaa40ab14ccc6714b53e16937cfc
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="copyrecordoptionsenum"></a>CopyRecordOptionsEnum
Задает поведение [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md) метод.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adCopyAllowEmulation**|4|Указывает, что *источника* поставщик пытается имитировать копии, с помощью загрузки и операций передачи, если этот метод завершается ошибкой из-за *назначения*выполняется на другом сервере или обслуживается другой Поставщик, чем *источника*. Обратите внимание, что различными возможностями поставщик может снижающим производительность или потере данных.|  
|**adCopyNonRecursive**|2|Копирует текущий каталог, но ни один из его подкаталогов в место назначения. Операция копирования не является рекурсивным.|  
|**adCopyOverWrite**|1|Перезаписывает файл или каталог, если *назначения* указывает на существующий файл или каталог.|  
|**adCopyUnspecified**|-1|По умолчанию. Выполняет операцию копирования по умолчанию: операция завершается неудачей, если целевой файл или каталог уже существует, а также рекурсивно копирует операции.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод CopyRecord (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)
