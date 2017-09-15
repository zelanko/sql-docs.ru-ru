---
title: "SQL модули | Документы Microsoft"
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
- SQL modules [ODBC]
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], modules
- modules [ODBC]
- SQL statements [ODBC], modules
ms.assetid: 07551472-87ee-4765-951f-1364ed32f0c0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f37ab932ef230d29a5db23aec920230de0443e37
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sql-modules"></a>SQL модули
Второй способ для отправки инструкций SQL в СУБД выполняется с помощью модулей. Коротко говоря модуля состоит из нескольких процедур, которые вызываются из узла, язык программирования. Каждая процедура содержит одну инструкцию SQL и данные передаются в и из процедуры через параметры.  
  
 Модуль может рассматриваться как библиотеку объектов, связанного с этим приложением. Однако точно как действия, остальной части приложения связаны зависит от реализации. Например процедуры может быть компилируются в код объекта и связаны непосредственно в код приложения, они могут компилируются и хранятся в СУБД и вызовы для доступа к идентификаторы плана, расположенные в коде приложения или может интерпретироваться во время выполнения.  
  
 Главным преимуществом модулей является полностью отдельные инструкции SQL на языке программирования. Теоретически возможно изменить одно без изменения другого и повторное создание их связей.
