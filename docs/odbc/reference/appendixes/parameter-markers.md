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
author: David-Engel
ms.author: v-daenge
ms.reviewer: ''
ms.openlocfilehash: 132473de586094f79dd34c999d44f6dd59aefaef
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303575"
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
