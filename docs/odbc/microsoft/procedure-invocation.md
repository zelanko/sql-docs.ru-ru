---
title: Процедура Вызова (англ.) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290775"
---
# <a name="procedure-invocation"></a>Вызов процедуры
При использовании драйвера Microsoft Access процедуры могут быть вызваны драйвером с помощью функции **S'LExecDirect** или **S'LPrepare** со следующим синтаксисом: «CALL *procedure-name* *(параметр,**параметр*...) » . Обратите внимание, что выражения не поддерживаются в качестве параметров для вызванной процедуры.  
  
 Если название процедуры включает тире, имя должно быть разграничено с задними кавычками (').  
  
 Параметризированный запрос можно вызвать с помощью предыдущего оператора.
