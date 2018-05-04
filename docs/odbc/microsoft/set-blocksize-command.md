---
title: Команда SET BLOCKSIZE | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- set blocksize command [ODBC]
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ab3510689a5f2c591453101e05dcfb5637c22cd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
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
