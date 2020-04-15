---
title: Совместимость (англ.) Документы Майкрософт
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
ms.openlocfilehash: 31b20a696c601ff91c591e4c717f468beca34e36
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306225"
---
# <a name="interoperability"></a>Взаимодействие
*Совместимость* — это способность одного приложения работать с различными DBMS. Необходимость написания общих, совместимых приложений была одним из основных факторов, ведущих к развитию ODBC. Однако совместимость — это не простой путь, который следовал от «не совместимого» до «полностью совместимого». Путь имеет много ветвей, и каждая из них требует компромиссов между функциями, скоростью, сложностью кода и временем разработки.  
  
 Процесс написания совместимого приложения следует нескольким шагам:  
  
1.  Решение о том, будет ли приложение использовать ODBC.  
  
2.  Для достижения этого уровня необходимо выбрать уровень совместимости и решить, какие компромиссы необходимы.  
  
3.  Написание совместимого кода и тестирование его как можно более полно.  
  
 Следует отметить, что совместимость является в первую очередь областью приложения писателя. Драйверы предназначены для работы с одним DBMS и, по определению, не совместимы. Они играют роль в совместимости, правильно внедряя и подвергая ODBC по одному DBMS.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Есть ли смысл использовать ODBC?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Выбор уровня взаимодействия](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Определение целевых СУБД и драйверов](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Оценка возможности использования функций базы данных](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Продолжительность цикла продукта](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Создание приложений с поддержкой взаимодействия](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Тестирование приложений с поддержкой взаимодействия](../../../odbc/reference/develop-app/testing-interoperable-applications.md)
