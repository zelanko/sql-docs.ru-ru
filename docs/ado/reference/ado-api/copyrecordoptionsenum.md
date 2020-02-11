---
title: Копирекордоптионсенум | Документация Майкрософт
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
ms.openlocfilehash: 6692125b7323bedc7a416e51555c373ef850ce0a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919373"
---
# <a name="copyrecordoptionsenum"></a>CopyRecordOptionsEnum
Задает поведение метода [копирекорд](../../../ado/reference/ado-api/copyrecord-method-ado.md) .  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адкопялловемулатион**|4|Указывает, что поставщик *источника* пытается имитировать копирование с помощью операций скачивания и отправки, если этот метод завершается сбоем из-за того, что *целевой объект*находится на другом сервере или обслуживается другим поставщиком, чем *источник*. Обратите внимание, что различные возможности поставщика могут препятствовать повышению производительности или потере данных.|  
|**адкопинонрекурсиве**|2|Копирует текущий каталог, но не все его подкаталоги в место назначения. Операция копирования не является рекурсивной.|  
|**адкопйоверврите**|1|Перезаписывает файл или каталог, если *целевой* объект указывает на существующий файл или каталог.|  
|**адкопюнспеЦифиед**|-1|По умолчанию. Выполняет операцию копирования по умолчанию: операция завершается ошибкой, если целевой файл или каталог уже существует, а операция копируется рекурсивно.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применяется к  
 [Метод CopyRecord (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)
