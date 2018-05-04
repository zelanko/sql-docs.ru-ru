---
title: Драйвер задачи | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC], tasks
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c7e351a84272e8ab9bd558e93e0d12bdc8275884
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="driver-tasks"></a>Драйвер задачи
Включать определенные задачи, выполняемые с помощью драйверов:  
  
-   Подключение и отключение от источника данных.  
  
-   Проверка ошибок функции не проверяется диспетчером драйверов.  
  
-   Запуск транзакций; Этот процесс прозрачен для приложения.  
  
-   Отправка инструкций SQL к источнику данных для выполнения. Изменить драйвер ODBC SQL для конкретных СУБД SQL; Это часто относится только к замене предложения escape, определенном ODBC с помощью СУБД SQL.  
  
-   Отправки и получение данных из источника данных, включая преобразование типов данных в соответствии с приложением.  
  
-   Сопоставления ошибок, связанных с СУБД ODBC SQLSTATE.
