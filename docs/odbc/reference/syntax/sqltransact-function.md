---
title: Функция SQLTransact | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLTransact
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTransact
helpviewer_keywords:
- SQLTransact function [ODBC]
ms.assetid: 496249e0-8eff-4c60-8358-5543bc3ead9c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 30aec4f94ca469f46ea4da6636c847d4a663dc3c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqltransact-function"></a>Функция SQLTransact
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: рекомендуется к использованию  
  
 **Сводка**  
 В ODBC 3. *x*, ODBC 2*.x* функция **SQLTransact** будет заменен **SQLEndTran**. Дополнительные сведения см. в разделе [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  Атрибут SQL_ASYNC_DBC_FUNCTION_ENABLE, которая была введена в ODBC 3.8, не поддерживается в **SQLTransact**. Приложения, использующие асинхронной операции на дескрипторе соединений необходимо использовать **SQLEndTran**.  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
