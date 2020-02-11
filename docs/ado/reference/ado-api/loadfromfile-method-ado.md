---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ce90b13a677246fb64462fbe691eb9e3efaa3c7f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918272"
---
# <a name="loadfromfile-method-ado"></a>Метод LoadFromFile (ADO)
Загружает содержимое существующего файла в [поток](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.LoadFromFileFileName  
```  
  
#### <a name="parameters"></a>Параметры  
 *Файлов*  
 **Строковое** значение, содержащее имя файла, загружаемого в **поток**. Имя *файла* может содержать любой допустимый путь и имя в формате UNC. Если указанный файл не существует, возникает ошибка времени выполнения.  
  
## <a name="remarks"></a>Remarks  
 Этот метод можно использовать для загрузки содержимого локального файла в объект **потока** . Это можно использовать для передачи содержимого локального файла на сервер.  
  
 Перед вызовом **лоадфромфиле**объект **потока** должен быть уже открыт. Этот метод не изменяет привязку объекта **потока** ; Он по-прежнему будет привязан к объекту, указанному в URL-адресе или **записи** , с которой был первоначально открыт **поток** .  
  
 **Лоадфромфиле** перезаписывает текущее содержимое объекта **потока** с данными, считанными из файла. Все существующие байты в **потоке** перезаписываются содержимым файла. Все ранее существующие и оставшиеся байты после [EOS](../../../ado/reference/ado-api/eos-property.md) , созданного **лоадфромфиле**, усекаются.  
  
 После вызова **лоадфромфиле**текущая координата устанавливается в начало **потока** ([позицией](../../../ado/reference/ado-api/position-property-ado.md) является 0).  
  
 Поскольку 2 байта можно добавить в начало потока для кодирования, размер потока может не совпадать с размером файла, из которого он был загружен.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
