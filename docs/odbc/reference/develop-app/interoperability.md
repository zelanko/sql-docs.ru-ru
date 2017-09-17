---
title: "Взаимодействие | Документы Microsoft"
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
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a96949b4ca739e382a547769f496576bf13db8b7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="interoperability"></a>Совместимость
*Взаимодействие* — это способность одного приложения для работы с многих различных DBMS. Потребность в написании универсальный, с возможностью взаимодействия приложений был одним из основных факторов, ведущих к разработке ODBC. Однако взаимодействия не простой путь из «не поддерживает возможность взаимодействия» для «полностью с возможностью взаимодействия.» Путь есть много ветвей, и каждый требует плюсы и минусы функции, скорости, сложности кода и времени разработки.  
  
 Процесс записи с возможностью взаимодействия приложения состоит из нескольких этапов:  
  
1.  Решить, будет ли приложение использовать ODBC.  
  
2.  Выбор уровня взаимодействия и решить, какие преимущества и недостатки необходимы для достижения этого уровня.  
  
3.  Написание кода с возможностью взаимодействия и как полностью его тестирование.  
  
 Следует отметить, что взаимодействие — в первую очередь это домен, разработчик приложения. Драйверы предназначены для работы с одной СУБД и по определению не являются функционально совместимыми. Они играют роль во взаимодействии с правильной реализации и предоставления ODBC через один СУБД.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Представляет собой ответ ODBC?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Выбор уровня взаимодействия](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Определение целевой СУБД и драйверов](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [При рассмотрении возможности базы данных для использования](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Длина цикла продукта](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Создание приложений с возможностью взаимодействия](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Тестирование приложений с возможностью взаимодействия](../../../odbc/reference/develop-app/testing-interoperable-applications.md)
