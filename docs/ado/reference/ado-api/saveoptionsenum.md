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
ms.openlocfilehash: 807a8d7e5757a2caf76f100a1ae51c4a8a3f4e98
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931147"
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
