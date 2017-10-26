---
title: "ЭКСКЛЮЗИВНОЕ команды SET | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 830cec1dbb87ae2bc4336d28d6112fd76b4db0ed
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="set-exclusive-command"></a>ЭКСКЛЮЗИВНОЕ команды SET
Указывает, открываются ли файлы таблиц для монопольного или общего использования в сети.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 Специальные возможности ограничения таблицы, в сети пользователь, открывший его открыть. Таблица недоступна для других пользователей в сети. SET МОНОПОЛЬНОГО ON также запрещает другим пользователям доступа только для чтения.  
  
 OFF  
 (По умолчанию для драйвера, значения по умолчанию для Visual FoxPro — ON для сеанса глобальных данных и OFF для сеанса личных данных.) Позволяет открыть в сети для общего доступа и изменение пользователем сети таблицу.  
  
## <a name="remarks"></a>Замечания  
 Чтобы изменить параметры УСТАНОВИТЬ МОНОПОЛЬНУЮ не изменяет состояние ранее открывавшихся таблиц. Например если таблица открывается с УСТАНОВИТЬ МОНОПОЛЬНУЮ присвоено значение ON и УСТАНОВИТЬ МОНОПОЛЬНУЮ позднее переводится в состояние OFF, таблице сохраняет состояние эксклюзивного использования.  
  
## <a name="see-also"></a>См. также:  
 [Диалоговое окно установки Visual FoxPro ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)

