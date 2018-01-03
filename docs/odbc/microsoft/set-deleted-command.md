---
title: "УДАЛЕННЫЕ команды SET | Документы Microsoft"
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
helpviewer_keywords: SET DELETED command [ODBC]
ms.assetid: 6b5e0086-156d-471d-8e7f-6c5fa9686cd5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 50364dfbbebb7b16b1438e3e17e0e1bbabc30cef
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="set-deleted-command"></a>УДАЛЕННЫЕ команды SET
Указывает, обрабатываются ли помеченные на удаление записи и ли они доступны для использования в других командах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET DELETED ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 (По умолчанию для драйвера, значение по умолчанию для Visual FoxPro — OFF). Указывает, что команды, работающих на записи (включая записи в связанных таблицах) с помощью области игнорировать помечен для удаления записей.  
  
 OFF  
 Указывает, что записи помечаются для удаления осуществляется с помощью команд, работающих на записи (включая записи в связанных таблицах) с помощью области.  
  
## <a name="remarks"></a>Remarks  
 Запросы, используйте (УДАЛЕННЫЕ) для проверки состояния записей можно оптимизировать с помощью технологии технологию Rushmore Visual FoxPro, если индексируется таблица, на (удалено).  
  
> [!IMPORTANT]  
>  SET DELETED игнорируется, если текущей области по умолчанию для команды, или если включить в области одной записи. Индекс всегда игнорирует значение УДАЛЕН и индексирует все записи в таблице.  
  
## <a name="see-also"></a>См. также:  
 [DELETE (команда SQL)](../../odbc/microsoft/delete-sql-command.md)
