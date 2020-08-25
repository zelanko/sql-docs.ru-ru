---
description: CopyRecordOptionsEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e38c2d3ffdf7ac088611f6a260224f46f80a7d7
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775754"
---
# <a name="copyrecordoptionsenum"></a>CopyRecordOptionsEnum
Задает поведение метода [копирекорд](./copyrecord-method-ado.md) .  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|**adCopyAllowEmulation**|4|Указывает, что поставщик *источника* пытается имитировать копирование с помощью операций скачивания и отправки, если этот метод завершается сбоем из-за того, что *целевой объект*находится на другом сервере или обслуживается другим поставщиком, чем *источник*. Обратите внимание, что различные возможности поставщика могут препятствовать повышению производительности или потере данных.|  
|**adCopyNonRecursive**|2|Копирует текущий каталог, но не все его подкаталоги в место назначения. Операция копирования не является рекурсивной.|  
|**adCopyOverWrite**|1|Перезаписывает файл или каталог, если *целевой* объект указывает на существующий файл или каталог.|  
|**adCopyUnspecified**|-1|По умолчанию. Выполняет операцию копирования по умолчанию: операция завершается ошибкой, если целевой файл или каталог уже существует, а операция копируется рекурсивно.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применение  
 [Метод CopyRecord (ADO)](./copyrecord-method-ado.md)