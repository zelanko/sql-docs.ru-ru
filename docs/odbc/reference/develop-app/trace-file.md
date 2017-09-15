---
title: "Файл трассировки | Документы Microsoft"
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
- trace files [ODBC]
- tracing options [ODBC], trace files
ms.assetid: ec97f949-126f-40a2-b67e-e74520a524cb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 82062fe767847023cd1aa6614173b292b0bff378
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="trace-file"></a>Файл трассировки
Приложение указывает файл трассировки, задав **TraceFile** ключевое слово в записи реестра Odbc.ini или вызвав **SQLSetConnectAttr** с атрибутом SQL_ATTR_TRACEFILE соединения. Если файл не существует, если трассировка включена, диспетчер драйверов будет создан файл. Каждое приложение должно иметь свой собственный файл трассировки выделенный во избежание конфликтов. Приложение может использовать более одного файла трассировки; Программа установки может предоставить пользователю возможность выбора файлов трассировки. Если трассировка включена динамически, приложения можно также отобразить результаты трассировки, а не ведения журнала в файл трассировки.  
  
 Файл трассировки содержит журнал каждого вызова функции ODBC, с типами данных и значения всех аргументов. Он регистрирует все входные функции и заносит в журнал все возвращенные функции с коды возврата и состояния ошибки.  
  
 В ODBC 3*.x*, параметры для функции соединения не предоставлены Библиотека трассировки.
