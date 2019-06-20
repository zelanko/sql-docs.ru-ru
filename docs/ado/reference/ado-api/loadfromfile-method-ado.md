---
title: Метод LoadFromFile (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_LoadFromFile
helpviewer_keywords:
- LoadFromFile method [ADO]
ms.assetid: b18d8d38-7354-4a94-b637-6ac035faa433
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ff7c5a2a2817fbe93d626ca7883107103edc58cd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66694715"
---
# <a name="loadfromfile-method-ado"></a>Метод LoadFromFile (ADO)
Загружает содержимое существующего файла в [Stream](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.LoadFromFileFileName  
```  
  
#### <a name="parameters"></a>Параметры  
 *FileName*  
 Объект **строка** значение, содержащее имя файла для загрузки в **Stream**. *Имя файла* может содержать любой допустимый путь и имя в формате UNC. Если указанный файл не существует, возникает ошибка времени выполнения.  
  
## <a name="remarks"></a>Примечания  
 Этот метод можно использовать для загрузки содержимого из локального файла в **Stream** объекта. Это может использоваться для загрузки содержимого из локального файла на сервер.  
  
 **Stream** объект должен быть уже открыт перед вызовом **LoadFromFile**. Этот метод не изменяет привязку **Stream** объекта; он будет по-прежнему быть привязан к объекту, заданному параметром URL-адрес или **записи** с помощью которого **Stream** изначально был Открыть.  
  
 **LoadFromFile** перезаписывает содержимое текущей **Stream** объекта с помощью данных, считанных из файла. Все существующие байты в **Stream** перезаписываются содержимое файла. Все ранее существующих и оставшиеся байты после [EOS](../../../ado/reference/ado-api/eos-property.md) созданные **LoadFromFile**, усекаются.  
  
 После вызова **LoadFromFile**, текущая позиция указывает на начало **Stream** ([позиции](../../../ado/reference/ado-api/position-property-ado.md) равно 0).  
  
 Так как 2 байта могут добавляться в начало потока для кодирования, размер потока может не совпадать размер файла, из которого она была загружена.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
