---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 807a8d7e5757a2caf76f100a1ae51c4a8a3f4e98
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931147"
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Указывает, следует ли создавать или перезаписывать файл при сохранении из объекта [потока](../../../ado/reference/ado-api/stream-object-ado.md) . Значения могут быть **адсавекреатенотексист** или **адсавекреатеоверврите**.  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адсавекреатенотексист**|1|По умолчанию. Создает новый файл, если файл, указанный в параметре *filename* , еще не существует.|  
|**адсавекреатеоверврите**|2|Перезаписывает файл данными из текущего открытого объекта **потока** , если файл, указанный параметром *filename* , уже существует. Если файл, указанный параметром *filename* , не существует, создается новый файл.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Применяется к  
 [Метод SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)
