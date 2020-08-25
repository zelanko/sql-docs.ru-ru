---
description: SaveOptionsEnum
title: Савеоптионсенум | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: edac11f61b003307703ec13daed8022b8af31bae
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777563"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Указывает, следует ли создавать или перезаписывать файл при сохранении из объекта [потока](./stream-object-ado.md) . Значения могут быть **адсавекреатенотексист** или **адсавекреатеоверврите**.  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|По умолчанию. Создает новый файл, если файл, указанный в параметре *filename* , еще не существует.|  
|**adSaveCreateOverWrite**|2|Перезаписывает файл данными из текущего открытого объекта **потока** , если файл, указанный параметром *filename* , уже существует. Если файл, указанный параметром *filename* , не существует, создается новый файл.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применение  
 [Метод SaveToFile](./savetofile-method.md)