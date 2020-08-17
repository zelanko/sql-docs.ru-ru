---
description: Вызов процедуры
title: Вызов процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e2643a36c834b577dfcecdcc81fd938a3a7d1018
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340450"
---
# <a name="procedure-invocation"></a>Вызов процедуры
При использовании драйвера Microsoft Access процедуры можно вызывать из драйвера с помощью функции **SQLExecDirect** или **SQLPrepare** со следующим синтаксисом: {Call *PROCEDURE-Name* [(*параметр*[,*Parameter*]...)]}. Обратите внимание, что выражения не поддерживаются в качестве параметров для вызываемой процедуры.  
  
 Если имя процедуры содержит тире, имя должно быть заключено в кавычки (').  
  
 Параметризованный запрос может быть вызван с помощью предыдущей инструкции.
