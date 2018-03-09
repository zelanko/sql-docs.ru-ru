---
title: "Расположение кэша | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 240d6162-4da6-4b1f-96c7-f379f4ecb16f
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f8d2c2083175bcccf1fba0157bcdf30c8b83af81
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="location-of-cache"></a>Расположение кэша
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 Библиотека курсоров кэширует данные в памяти и в Windows® временных файлов. Это ограничивает размер результирующего набора, библиотеку курсоров может обрабатывать только объемом свободного места. Временный файл используется, если для кэширования данных будет пересекает границы сегмента, если вставляется в конце кэш библиотеки курсоров. Вместо этого для кэширования данных добавляется вместо последней сохраненной блок данных в кэше. Последняя сохраненная блок данных сохраняется во временном файле. Если библиотека курсоров аварийном завершении, например при сбое питания, его можно оставить временные файлы на диске. Они называются ~ CTT*nnnn*.tmp и являются созданы в текущем каталоге.  
  
> [!NOTE]  
>  Если библиотека курсоров в Microsoft® WindowsNT® или Windows 2000 пытается кэшировать данные во временном файле в текущем каталоге приложения, запущенного из папки только для чтения или компакт-дисков (например, образец библиотеки классов Microsoft Foundation) SQLSTATE HY000 будет возвращено (Общая ошибка-не удалось создать файловый буфер).
