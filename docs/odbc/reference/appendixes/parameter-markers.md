---
description: Маркеры параметров
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
ms.openlocfilehash: a585fb983a8f1662cdd42d361f106a76bfd47cb6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483237"
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
