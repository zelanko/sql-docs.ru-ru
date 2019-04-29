---
title: Команда SET BLOCKSIZE | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: e904d341513047b3940cf5b3fc2ba9538cdb5c8f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127846"
---
# <a name="set-blocksize-command"></a>Команда SET BLOCKSIZE
Указывает, распределении дискового пространства для хранения поля типа memo.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>Аргументы  
 *nBytes*  
 Указывает размер блока, в которой выделяется место на диске для полей типа memo. Если *nBytes* равно 0, места на диске выделяется один байт (блоков с размером 1 байт). Если *nBytes* является целым числом от 1 до 32, места на диске выделяется в блоках *nBytes* умноженному 512 байт. Если *nBytes* длиннее 32 разрядов, выделения места на диске в виде блоков *nBytes* байт. Если указать значение для размера блока, больше 32, можно сохранить значительное дисковое пространство.  
  
## <a name="remarks"></a>Примечания  
 ЗАДАТЬ размер блока по умолчанию — 64. Чтобы сбросить размер блока с другим значением, после создания файла, присвоить новое значение и затем использовать КОПИРОВАНИЯ для создания новой таблицы. Новая таблица имеет размер указанного блока.
