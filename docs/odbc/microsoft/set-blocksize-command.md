---
title: Команда SET BLOCKSize (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3eb9fbe9df90f7ddafebc6baa029164a578a6da3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300904"
---
# <a name="set-blocksize-command"></a>Команда SET BLOCKSIZE
Определяет, как выделено дисковое пространство для хранения полей памяток.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>Аргументы  
 *nБайт*  
 Определяет размер блока, в котором выделяется дисковое пространство для полей памятки. Если *nBytes* равен 0, дисковое пространство выделяется в одиночных байтах (блоки 1 байт). Если *nBytes* является множеством между 1 и 32, дисковое пространство выделяется блоками *nBytes* байтов, умноженных на 512. Если *nBytes* больше 32, дисковое пространство выделяется блоками *байтов nBytes.* Если указать значение размера блока, превышающее 32, можно сэкономить значительное пространство диска.  
  
## <a name="remarks"></a>Remarks  
 Значение по умолчанию для SET BLOCKSize составляет 64. Чтобы сбросить размер блока в другое значение после создания файла, установите его на новое значение, а затем используйте COPY для создания новой таблицы. Новая таблица имеет указанный размер блока.
