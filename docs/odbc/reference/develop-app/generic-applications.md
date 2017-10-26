---
title: "Универсальные приложения | Документы Microsoft"
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
- interoperability [ODBC], generic applications
- interoperability [ODBC], levels
- generic applications [ODBC]
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 991c4eb6a1fb9b7974272a0df9eba2c022e4d177
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="generic-applications"></a>Универсальные приложения
Универсальные приложения иногда выполнить задачу жестко, например электронных таблицах извлечение данных из базы данных. Они также может выполнять разнообразные задачи, определяемые пользователем, например приложения универсальный запрос, чтобы пользователи могли вводить и выполнять инструкции SQL. Что универсальные приложения имеют общий — что они должны работать со множеством различных DBMS и что разработчик не может заранее эти СУБД, которые будут.  
  
 Таким образом универсальные приложения должны иметь возможность взаимодействия. Разработчику необходимо внести много вариантов, снижая взаимодействие для компонентов и необходимо написать код, который ожидает, что драйверы для поддержки широкий набор функций. Хотя универсальные приложения может настроить для работы с распространенных СУБД, они редко содержит специфические для драйвера или СУБД определенного кода.

