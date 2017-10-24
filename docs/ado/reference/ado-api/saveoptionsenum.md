---
title: "SaveOptionsEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- SaveOptionsEnum
helpviewer_keywords:
- SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 97f3d76d9fed33de5ba79d84a062891316c70ae0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Указывает, следует создать или перезаписан при сохранении из файла [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта. Значения могут быть **adSaveCreateNotExist** или **adSaveCreateOverWrite**...  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|По умолчанию. Создает новый файл, если файл, указанный параметром *FileName* параметр еще не существует.|  
|**adSaveCreateOverWrite**|2|Перезаписывает файл с данными из открытых в настоящее время **поток** объекта, если файл, указанный параметром *Filename* уже существует. Если файл, указанный параметром *Filename* параметр не существует, создается новый файл.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)

