---
title: Команда установки блока размерности | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set blocksize command [ODBC]
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4fe84a470f5e877c73701168394cd85d75253fb7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67997758"
---
# <a name="set-blocksize-command"></a>Команда SET BLOCKSIZE
Указывает, как выделяется место на диске для хранения полей MEMO.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>Аргументы  
 *nBytes*  
 Указывает размер блока, в котором выделяется место на диске для полей MEMO. Если *nBytes* имеет значение 0, место на диске выделяется в виде одного байта (блоков из 1 байта). Если *nBytes* представляет собой целое число от 1 до 32, то место на диске выделяется в блоках из *nBytes* байт, умноженных на 512. Если *nBytes* больше 32, то место на диске выделяется в блоках *nBytes* байт. Если задать значение размера блока, превышающее 32, можно сэкономить место на диске.  
  
## <a name="remarks"></a>Remarks  
 Значение по умолчанию для SET размер блока — 64. Чтобы сбросить размер блока до другого значения после создания файла, присвойте ему новое значение, а затем используйте COPY для создания новой таблицы. Новая таблица имеет указанный размер блока.
