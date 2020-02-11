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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915462"
---
# <a name="driver-tasks"></a>Задачи драйвера
К конкретным задачам, выполняемым драйверами, относятся:  
  
-   Подключение к источнику данных и отключение от него.  
  
-   Проверка ошибок функций, не проверенных диспетчером драйверов.  
  
-   Запуск транзакций; Это прозрачно для приложения.  
  
-   Отправка инструкций SQL в источник данных для выполнения. Драйвер должен изменить SQL ODBC на SQL, зависящий от СУБД; Это часто ограничивается заменой escape-предложений, определенных ODBC, с помощью SQL, относящегося к СУБД.  
  
-   Отправка и получение данных из источника данных, включая преобразование типов данных, указанных в приложении.  
  
-   Сопоставление ошибок, связанных с СУБД, с ODBC SQLSTATE.
