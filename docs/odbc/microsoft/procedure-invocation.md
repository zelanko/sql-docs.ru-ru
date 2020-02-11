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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bc37ef6d268dba71f8270909ea9c5b938ef3ee75
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070495"
---
# <a name="procedure-invocation"></a>Вызов процедуры
При использовании драйвера Microsoft Access процедуры можно вызывать из драйвера с помощью функции **SQLExecDirect** или **SQLPrepare** со следующим синтаксисом: {Call *PROCEDURE-Name* [(*параметр*[,*Parameter*]...)]}. Обратите внимание, что выражения не поддерживаются в качестве параметров для вызываемой процедуры.  
  
 Если имя процедуры содержит тире, имя должно быть заключено в кавычки (').  
  
 Параметризованный запрос может быть вызван с помощью предыдущей инструкции.
