---
description: Метод LoadFromFile (ADO)
title: Метод Лоадфромфиле (ADO) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2f07bd7bc6b04dac8c5b352cc6281ce4eb851d3d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443356"
---
# <a name="loadfromfile-method-ado"></a>Метод LoadFromFile (ADO)
Загружает содержимое существующего файла в [поток](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.LoadFromFileFileName  
```  
  
#### <a name="parameters"></a>Параметры  
 *FileName*  
 **Строковое** значение, содержащее имя файла, загружаемого в **поток**. Имя *файла* может содержать любой допустимый путь и имя в формате UNC. Если указанный файл не существует, возникает ошибка времени выполнения.  
  
## <a name="remarks"></a>Remarks  
 Этот метод можно использовать для загрузки содержимого локального файла в объект **потока** . Это можно использовать для передачи содержимого локального файла на сервер.  
  
 Перед вызовом **лоадфромфиле**объект **потока** должен быть уже открыт. Этот метод не изменяет привязку объекта **потока** ; Он по-прежнему будет привязан к объекту, указанному в URL-адресе или **записи** , с которой был первоначально открыт **поток** .  
  
 **Лоадфромфиле** перезаписывает текущее содержимое объекта **потока** с данными, считанными из файла. Все существующие байты в **потоке** перезаписываются содержимым файла. Все ранее существующие и оставшиеся байты после [EOS](../../../ado/reference/ado-api/eos-property.md) , созданного **лоадфромфиле**, усекаются.  
  
 После вызова **лоадфромфиле**текущая координата устанавливается в начало **потока** ([позицией](../../../ado/reference/ado-api/position-property-ado.md) является 0).  
  
 Поскольку 2 байта можно добавить в начало потока для кодирования, размер потока может не совпадать с размером файла, из которого он был загружен.  
  
## <a name="applies-to"></a>Применение  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
