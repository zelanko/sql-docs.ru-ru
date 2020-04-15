---
title: Задачи драйвера (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294204"
---
# <a name="driver-tasks"></a>Задачи драйвера
Конкретные задачи, выполняемые водителями включают в себя:  
  
-   Подключение и отключение от источника данных.  
  
-   Проверка ошибок функции, не проверенных менеджером драйвера.  
  
-   Исвеженстом сделок; это прозрачно для приложения.  
  
-   Отправка инструкций по S'L в источник данных для выполнения. Драйвер должен изменить ODBC S'L в dBMS-специфический S'L; это часто ограничивается заменой эвакуационных оговорок, определенных ODBC, с помощью DBMS-специфического S'L.  
  
-   Отправка данных и извлечение данных из источника данных, включая преобразование типов данных, указанных в приложении.  
  
-   Отображение ошибок, специфических DBMS, с ODBC S'LSTATEs.
