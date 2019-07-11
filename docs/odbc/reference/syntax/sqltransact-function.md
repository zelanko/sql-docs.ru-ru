---
title: Функция SQLTransact | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ad40522bd9f97c72a5d0a71d089b9e7c98a7d6b
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793623"
---
# <a name="sqltransact-function"></a>Функция SQLTransact
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 1.0 ODBC: Устарело  
  
 **Сводка**  
 В ODBC *3.x*, ODBC *2.x* функция **SQLTransact** был заменен классом **SQLEndTran**. Дополнительные сведения см. в разделе [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  Атрибут SQL_ASYNC_DBC_FUNCTION_ENABLE, которая была введена в ODBC 3.8, не поддерживается в **SQLTransact**. Приложения с помощью асинхронной операции для дескриптора соединения должны использовать **SQLEndTran**.  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
