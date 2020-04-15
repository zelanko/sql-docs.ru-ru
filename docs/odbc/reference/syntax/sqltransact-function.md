---
title: Функция S'LTransact (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c7a4f1da36a7c233e9a1b5832ee83e86a5c1f77d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287084"
---
# <a name="sqltransact-function"></a>Функция SQLTransact
**Соответствия**  
 Версия Введена: Соответствие стандартам ODBC 1.0: Deprecated  
  
 **Сводка**  
 В ODBC *3.x*, функция ODBC *2.x* **S'LTransact** была заменена **на S'LEndTran**. Для получения более подробной информации, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)  
  
> [!NOTE]  
>  Атрибут SQL_ASYNC_DBC_FUNCTION_ENABLE, который был введен в ODBC 3.8, не поддерживается **S'LTransact**. Приложения, использующие асинхронную операцию на ручке соединения, должны использовать **S'LEndTran.**  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
