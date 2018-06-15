---
title: УДАЛЕННЫЕ команды SET | Документы Microsoft
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
- SET DELETED command [ODBC]
ms.assetid: 6b5e0086-156d-471d-8e7f-6c5fa9686cd5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74cd0c5752728320acf09768d876bae37b6e193b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32901689"
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
  
## <a name="remarks"></a>Замечания  
 Запросы, используйте (УДАЛЕННЫЕ) для проверки состояния записей можно оптимизировать с помощью технологии технологию Rushmore Visual FoxPro, если индексируется таблица, на (удалено).  
  
> [!IMPORTANT]  
>  SET DELETED игнорируется, если текущей области по умолчанию для команды, или если включить в области одной записи. Индекс всегда игнорирует значение УДАЛЕН и индексирует все записи в таблице.  
  
## <a name="see-also"></a>См. также  
 [DELETE (команда SQL)](../../odbc/microsoft/delete-sql-command.md)
