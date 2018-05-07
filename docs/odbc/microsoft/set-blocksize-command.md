---
title: Команда SET BLOCKSIZE | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- set blocksize command [ODBC]
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 85b9df4f40c68d68ea28a4bfad006105e4a98d7b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="set-blocksize-command"></a>BLOCKSIZE команды SET
Задает распределение места на диске для хранения поля типа memo.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>Аргументы  
 *nBytes*  
 Указывает размер блока, в котором выделения места на диске для полей типа memo. Если *nBytes* равно 0, дисковое пространство выделяется один байт (блоки данных размером 1 байт). Если *nBytes* является целым числом от 1 до 32, места на диске выделяется в блоках *nBytes* умноженный 512 байт. Если *nBytes* больше, чем 32, выделить место на диске в виде блоков *nBytes* байт. Если указать значение для размера блока, больше, чем 32, можно сохранить значительного места на диске.  
  
## <a name="remarks"></a>Замечания  
 ЗАДАЙТЕ размер блока по умолчанию — 64. Чтобы сбросить размер блока другое значение, после создания файла, присваивается новое значение и создать новую таблицу с помощью команды Копировать. Новая таблица имеет размер указанного блока.
