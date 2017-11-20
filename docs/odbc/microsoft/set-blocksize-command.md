---
title: "Команда SET BLOCKSIZE | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- set blocksize command [ODBC]
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d0c98afd9479e1a7de4f7a14834909962f274f1e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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

