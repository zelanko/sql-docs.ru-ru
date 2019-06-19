---
title: SaveOptionsEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SaveOptionsEnum
helpviewer_keywords:
- SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 537c5bfa6e1da125b562d4cc26820a2fcb5618fc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711376"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Указывает, следует ли создать или перезаписан при сохранении из файла [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта. Значения могут быть **adSaveCreateNotExist** или **adSaveCreateOverWrite**...  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|По умолчанию. Создает новый файл, если файл, заданный параметром *FileName* параметр еще не существует.|  
|**adSaveCreateOverWrite**|2|Перезаписывает файл с данными из уже открытой **Stream** объект, если файл, заданный параметром *Filename* параметр уже существует. Если файл, заданный параметром *Filename* параметр не существует, создается новый файл.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Эти константы не имеют эквивалентов ADO и WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)
