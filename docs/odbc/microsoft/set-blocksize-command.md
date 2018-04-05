---
title: Команда SET BLOCKSIZE | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- set blocksize command [ODBC]
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8e2fe90c50d87cea5b949787a6504479c2670e14
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
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
  
## <a name="remarks"></a>Remarks  
 ЗАДАЙТЕ размер блока по умолчанию — 64. Чтобы сбросить размер блока другое значение, после создания файла, присваивается новое значение и создать новую таблицу с помощью команды Копировать. Новая таблица имеет размер указанного блока.
