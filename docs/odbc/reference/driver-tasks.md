---
title: Драйвер задачи | Документы Microsoft
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
- ODBC architecture [ODBC], drivers
- drivers [ODBC], tasks
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b8ea61df89eb6f4e21a57e71a4277d56b16add5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915709"
---
# <a name="driver-tasks"></a>Драйвер задачи
Включать определенные задачи, выполняемые с помощью драйверов:  
  
-   Подключение и отключение от источника данных.  
  
-   Проверка ошибок функции не проверяется диспетчером драйверов.  
  
-   Запуск транзакций; Этот процесс прозрачен для приложения.  
  
-   Отправка инструкций SQL к источнику данных для выполнения. Изменить драйвер ODBC SQL для конкретных СУБД SQL; Это часто относится только к замене предложения escape, определенном ODBC с помощью СУБД SQL.  
  
-   Отправки и получение данных из источника данных, включая преобразование типов данных в соответствии с приложением.  
  
-   Сопоставления ошибок, связанных с СУБД ODBC SQLSTATE.
