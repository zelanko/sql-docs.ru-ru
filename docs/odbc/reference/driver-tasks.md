---
title: "Драйвер задачи | Документы Microsoft"
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
- ODBC architecture [ODBC], drivers
- drivers [ODBC], tasks
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 331e3aee3a4a60cbfa1a1308b71da80bf9772f23
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="driver-tasks"></a>Драйвер задачи
Включать определенные задачи, выполняемые с помощью драйверов:  
  
-   Подключение и отключение от источника данных.  
  
-   Проверка ошибок функции не проверяется диспетчером драйверов.  
  
-   Запуск транзакций; Этот процесс прозрачен для приложения.  
  
-   Отправка инструкций SQL к источнику данных для выполнения. Изменить драйвер ODBC SQL для конкретных СУБД SQL; Это часто относится только к замене предложения escape, определенном ODBC с помощью СУБД SQL.  
  
-   Отправки и получение данных из источника данных, включая преобразование типов данных в соответствии с приложением.  
  
-   Сопоставления ошибок, связанных с СУБД ODBC SQLSTATE.
