---
title: Loadfromfile-метод (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_LoadFromFile
helpviewer_keywords:
- LoadFromFile method [ADO]
ms.assetid: b18d8d38-7354-4a94-b637-6ac035faa433
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ade472c2b209c3e2d03a172eb66ad7a550f31ef5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="loadfromfile-method-ado"></a>Loadfromfile-метод (ADO)
Загружает содержимое существующего файла в [поток](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Stream.LoadFromFileFileName  
```  
  
#### <a name="parameters"></a>Параметры  
 *FileName*  
 Объект **строка** значение, содержащее имя файла для загрузки в **поток**. *Имя файла* может содержать любой допустимый путь и имя в формате UNC. Если указанный файл не существует, возникает ошибка времени выполнения.  
  
## <a name="remarks"></a>Замечания  
 Этот метод можно использовать для загрузки содержимого из локального файла в **поток** объекта. Это можно использовать для загрузки содержимого из локального файла на сервер.  
  
 **Поток** объект должен быть уже открыт перед вызовом метода **LoadFromFile**. Этот метод не изменяет привязку **поток** объекта; он будет по-прежнему привязан к объекту, определяемому URL-адрес или **запись** с помощью которого **поток** изначально Открыть.  
  
 **LoadFromFile** перезаписывает содержимое текущей **поток** объект с данные, считанные из файла. Любые существующие байты в **поток** перезаписываются содержимое файла. Все ранее существующие и оставшиеся байты после [электрической ПЕРЕГРУЗКИ](../../../ado/reference/ado-api/eos-property.md) созданные **LoadFromFile**, усекаются.  
  
 После вызова **LoadFromFile**, имеет значение текущей позиции в начало **поток** ([позиции](../../../ado/reference/ado-api/position-property-ado.md) равно 0).  
  
 Так как 2 байта могут быть добавлены в начало потока для кодирования, размер потока может не совпадать размер файла, из которого она была загружена.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
