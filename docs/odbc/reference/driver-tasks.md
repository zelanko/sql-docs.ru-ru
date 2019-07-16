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
ms.openlocfilehash: 2e2ed50ac3f9e914953abdd64907199a5f978af2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915462"
---
# <a name="driver-tasks"></a>Задачи драйвера
Определенные задачи, выполняемые драйверами включают:  
  
-   Подключение и отключение от источника данных.  
  
-   Проверка ошибки функций, не проверяется диспетчером драйверов.  
  
-   Запуск транзакций; Этот процесс прозрачен для приложения.  
  
-   Отправка инструкций SQL к источнику данных для выполнения. Изменить драйвер ODBC SQL для конкретных СУБД SQL; часто это ограничение для замены предложения escape, определенном ODBC с СУБД SQL.  
  
-   Отправки и извлечения данных из источника данных, в том числе преобразование типов данных, определенной для приложения.  
  
-   Сопоставления ошибок, связанных с СУБД ODBC SQLSTATE.
