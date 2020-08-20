---
description: Взаимодействие
title: Взаимодействие | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a404ee6de56cbd8b5605eca640fdf0e065f16d79
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476616"
---
# <a name="interoperability"></a>Совместимость
*Взаимодействие* — это способность одного приложения использовать множество различных СУБД. Необходимость написания универсальных, взаимодействующих приложений была одним из основных факторов, ведущих к разработке ODBC. Однако взаимодействие не является простым путем, за которым следует "не совместимый" с "полностью совместимым". Путь имеет много ветвей, и для каждого из них требуются компромиссы между функциями, скоростью, сложностью кода и временем разработки.  
  
 Процесс написания приложения, поддерживающего взаимодействие, выполняется за несколько шагов:  
  
1.  Принятие решения о том, будет ли приложение использовать ODBC.  
  
2.  Выберите уровень взаимодействия и решите, какие компромиссы необходимы для достижения этого уровня.  
  
3.  Написание кода для взаимодействия и его тестирование как можно более полно.  
  
 Следует отметить, что взаимодействие в основном является доменом модуля записи приложения. Драйверы предназначены для работы с одной СУБД и, по определению, не совместимы. Они играют роль в взаимодействии, правильно реализуя и предоставляя ODBC через одну СУБД.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Есть ли смысл использовать ODBC?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Выбор уровня взаимодействия](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Определение целевых СУБД и драйверов](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Оценка возможности использования функций базы данных](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Продолжительность цикла продукта](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Создание приложений с поддержкой взаимодействия](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Тестирование приложений с поддержкой взаимодействия](../../../odbc/reference/develop-app/testing-interoperable-applications.md)
