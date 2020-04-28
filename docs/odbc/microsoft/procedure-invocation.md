---
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
ms.openlocfilehash: 32617cdb753f5fc1b9c52520cb609d2902137b54
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81290775"
---
# <a name="procedure-invocation"></a>Вызов процедуры
При использовании драйвера Microsoft Access процедуры можно вызывать из драйвера с помощью функции **SQLExecDirect** или **SQLPrepare** со следующим синтаксисом: {Call *PROCEDURE-Name* [(*параметр*[,*Parameter*]...)]}. Обратите внимание, что выражения не поддерживаются в качестве параметров для вызываемой процедуры.  
  
 Если имя процедуры содержит тире, имя должно быть заключено в кавычки (').  
  
 Параметризованный запрос может быть вызван с помощью предыдущей инструкции.
