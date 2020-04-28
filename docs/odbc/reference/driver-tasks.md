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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1b30df63a3c955d2ed074ab13649ea55c21a6da7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294204"
---
# <a name="driver-tasks"></a>Задачи драйвера
К конкретным задачам, выполняемым драйверами, относятся:  
  
-   Подключение к источнику данных и отключение от него.  
  
-   Проверка ошибок функций, не проверенных диспетчером драйверов.  
  
-   Запуск транзакций; Это прозрачно для приложения.  
  
-   Отправка инструкций SQL в источник данных для выполнения. Драйвер должен изменить SQL ODBC на SQL, зависящий от СУБД; Это часто ограничивается заменой escape-предложений, определенных ODBC, с помощью SQL, относящегося к СУБД.  
  
-   Отправка и получение данных из источника данных, включая преобразование типов данных, указанных в приложении.  
  
-   Сопоставление ошибок, связанных с СУБД, с ODBC SQLSTATE.
