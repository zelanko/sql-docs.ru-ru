---
title: Универсальные приложения | Документы Microsoft
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
- interoperability [ODBC], generic applications
- interoperability [ODBC], levels
- generic applications [ODBC]
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae9643de106e11865505483d84f2253fb9511227
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="generic-applications"></a>Универсальные приложения
Универсальные приложения иногда выполнить задачу жестко, например электронных таблицах извлечение данных из базы данных. Они также может выполнять разнообразные задачи, определяемые пользователем, например приложения универсальный запрос, чтобы пользователи могли вводить и выполнять инструкции SQL. Что универсальные приложения имеют общий — что они должны работать со множеством различных DBMS и что разработчик не может заранее эти СУБД, которые будут.  
  
 Таким образом универсальные приложения должны иметь возможность взаимодействия. Разработчику необходимо внести много вариантов, снижая взаимодействие для компонентов и необходимо написать код, который ожидает, что драйверы для поддержки широкий набор функций. Хотя универсальные приложения может настроить для работы с распространенных СУБД, они редко содержит специфические для драйвера или СУБД определенного кода.
