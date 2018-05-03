---
title: SaveOptionsEnum | Документы Microsoft
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
- SaveOptionsEnum
helpviewer_keywords:
- SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ebd08388e2b658c6a4b5d85000d48dd4fe77c671
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Указывает, следует создать или перезаписан при сохранении из файла [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта. Значения могут быть **adSaveCreateNotExist** или **adSaveCreateOverWrite**...  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|По умолчанию. Создает новый файл, если файл, указанный параметром *FileName* параметр еще не существует.|  
|**adSaveCreateOverWrite**|2|Перезаписывает файл с данными из открытых в настоящее время **поток** объекта, если файл, указанный параметром *Filename* уже существует. Если файл, указанный параметром *Filename* параметр не существует, создается новый файл.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)
