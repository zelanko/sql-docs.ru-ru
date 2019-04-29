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
manager: craigg
ms.openlocfilehash: cda6719eb46a4a05222bd54062e6cab98459d7dc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181774"
---
# <a name="parameter-markers"></a>Маркеры параметров
В соответствии со спецификацией SQL-92 приложения не удается разместить маркеры параметров в следующих расположениях. Более полный список см. в спецификации SQL-92.  
  
-   В **ВЫБЕРИТЕ** списка  
  
-   Как *выражения* в *предикат сравнения*  
  
-   Так как оба операнда бинарного оператора  
  
-   В качестве первого и второго операндов из **BETWEEN** операции  
  
-   Как первый и третий операнды **BETWEEN** операции  
  
-   Как выражение и первое значение **IN** операции  
  
-   Как операнд унарного + или - операции  
  
-   В качестве аргумента *Справочник по функциям набора*  
  
 Дополнительные сведения о маркерах см. в спецификации SQL-92. Дополнительные сведения о параметрах см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md).
