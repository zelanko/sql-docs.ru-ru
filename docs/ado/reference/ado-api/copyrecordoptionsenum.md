---
title: CopyRecordOptionsEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CopyRecordOptionsEnum
helpviewer_keywords:
- CopyRecordOptionsEnum enumeration [ADO]
ms.assetid: 2fa4eec5-d50b-4fd3-8ae7-40af441ba12b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a944d3f82940d9364312fb8033ec8b8937b0c49c
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66695762"
---
# <a name="copyrecordoptionsenum"></a>CopyRecordOptionsEnum
Задает поведение [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md) метод.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adCopyAllowEmulation**|4|Указывает, что *источника* поставщик пытается имитировать копии, с помощью загрузки и отправки операций в том случае, если этот метод завершается ошибкой из-за *назначения*выполняется на другом сервере или обслуживается другим Поставщик, чем *источника*. Обратите внимание, что разными возможностями поставщик может снижающим производительность или потере данных.|  
|**adCopyNonRecursive**|2|Копирует текущий каталог, но ни один из его подкаталогов в место назначения. Операция копирования не является рекурсивным.|  
|**adCopyOverWrite**|1|Перезаписывает файл или каталог, если *назначения* указывает на существующий файл или каталог.|  
|**adCopyUnspecified**|-1|По умолчанию. Выполняет операцию копирования по умолчанию: Операция завершается неудачей, если целевой файл или каталог уже существует и рекурсивно копирует операции.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Эти константы не имеют эквивалентов ADO и WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод CopyRecord (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)
