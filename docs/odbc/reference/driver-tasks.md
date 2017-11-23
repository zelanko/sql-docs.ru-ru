---
title: "Драйвер задачи | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC], tasks
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e814f2780baecee5c33edd38f6def2f30abafddd
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="driver-tasks"></a>Драйвер задачи
Включать определенные задачи, выполняемые с помощью драйверов:  
  
-   Подключение и отключение от источника данных.  
  
-   Проверка ошибок функции не проверяется диспетчером драйверов.  
  
-   Запуск транзакций; Этот процесс прозрачен для приложения.  
  
-   Отправка инструкций SQL к источнику данных для выполнения. Изменить драйвер ODBC SQL для конкретных СУБД SQL; Это часто относится только к замене предложения escape, определенном ODBC с помощью СУБД SQL.  
  
-   Отправки и получение данных из источника данных, включая преобразование типов данных в соответствии с приложением.  
  
-   Сопоставления ошибок, связанных с СУБД ODBC SQLSTATE.
