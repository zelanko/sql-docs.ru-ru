---
title: "ЭКСКЛЮЗИВНОЕ команды SET | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f5aa039c9af4b3dfbabce2647408be7f612c80f3
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
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
 [Диалоговое окно настройки ODBC для Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
