---
title: Маркеры параметров | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- parameter markers [ODBC]
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.openlocfilehash: acb8d5f9687798bc0efa514ee8646b16140fcd36
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68100585"
---
# <a name="parameter-markers"></a>Маркеры параметров
В соответствии со спецификацией SQL-92 приложение не может размещать маркеры параметров в следующих местах. Более полный список см. в спецификации SQL-92.  
  
-   В списке **выбора**  
  
-   Как оба *выражения* в *предикате сравнения*  
  
-   Как оба операнда бинарного оператора  
  
-   В качестве первого и второго операнда **между** операциями  
  
-   Как первый и третий операнды **между** операциями  
  
-   Как выражение и первое значение **в** операции  
  
-   Как операнд унарной операции + или-  
  
-   В качестве аргумента для *ссылки Set-Function*  
  
 Дополнительные сведения о маркерах параметров см. в спецификации SQL-92. Дополнительные сведения о параметрах см. в разделе [Параметры инструкции](../../../odbc/reference/develop-app/statement-parameters.md).
