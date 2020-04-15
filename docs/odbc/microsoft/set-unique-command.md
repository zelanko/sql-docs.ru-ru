---
title: Команда СЕТ УНИКУЕ (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7d3d37509450d1305891100b37bfd1ad026166e8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300844"
---
# <a name="set-unique-command"></a>Команда SET UNIQUE
Уточняется, сохраняются ли в файле индекса записи с дублирующими значениями ключевых индексов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 Условляет, что любая запись с дубликатом значения ключевого индекса не будет включена в файл индекса. В файл индекса включена только первая запись с исходным значением ключа индекса.  
  
 OFF  
 (По умолчанию.) Условляет, что записи с дублирующими значениями ключевых индексов будут включены в файл индекса.  
  
## <a name="remarks"></a>Remarks  
 Файл индекса сохраняет настройки SET Unique при выпуске REINDEX. Для получения дополнительной информации [см.](../../odbc/microsoft/index-command.md)
