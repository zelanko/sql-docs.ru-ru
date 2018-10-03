---
title: Задачи драйвера | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC], tasks
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee695c62fc60b2ebb0ae9bb33ef9008ba617b49a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772638"
---
# <a name="driver-tasks"></a>Задачи драйвера
Определенные задачи, выполняемые драйверами включают:  
  
-   Подключение и отключение от источника данных.  
  
-   Проверка ошибки функций, не проверяется диспетчером драйверов.  
  
-   Запуск транзакций; Этот процесс прозрачен для приложения.  
  
-   Отправка инструкций SQL к источнику данных для выполнения. Изменить драйвер ODBC SQL для конкретных СУБД SQL; часто это ограничение для замены предложения escape, определенном ODBC с СУБД SQL.  
  
-   Отправки и извлечения данных из источника данных, в том числе преобразование типов данных, определенной для приложения.  
  
-   Сопоставления ошибок, связанных с СУБД ODBC SQLSTATE.
