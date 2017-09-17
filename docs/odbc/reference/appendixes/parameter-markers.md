---
title: "Маркеры параметров | Документы Microsoft"
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
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- parameter markers [ODBC]
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c2c8708c18abee3609fc0b01f6ccd2e0362e5706
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="parameter-markers"></a>Маркеры параметров
В соответствии со спецификацией SQL-92 приложению не удается разместить маркеры параметров в следующих местах. Более полный список см. в спецификации SQL-92.  
  
-   В **ВЫБЕРИТЕ** списка  
  
-   Как *выражений* в *предикат сравнения*  
  
-   Как оба операнда бинарного оператора  
  
-   В качестве первого и второго операнда из **BETWEEN** операции  
  
-   Как первый и третий операнды **BETWEEN** операции  
  
-   Как выражение и первое значение **в** операции  
  
-   В качестве операнда унарный + или – операции  
  
-   В качестве аргумента *ссылка на функцию для набора*  
  
 Дополнительные сведения о маркерах см. в спецификации SQL-92. Дополнительные сведения о параметрах см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md).
