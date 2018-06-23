---
title: Выделение дескриптора среды | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 89bf5353b37858c12212eed4567e0bae7f49d77f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098196"
---
# <a name="allocating-an-environment-handle"></a>Выделение дескриптора среды
  Прежде чем в приложении появится возможность вызвать какую-либо функцию ODBC, необходимо инициализировать среду ODBC и выделить дескриптор среды. Это — глобальный дескриптор контекста и заполнитель для других дескрипторов в ODBC. Это делается путем вызова **SQLAllocHandle** с *HandleType* параметр значение SQL_HANDLE_ENV и *InputHandle* установленным в значение SQL_NULL_HANDLE.  
  
 После выделения дескриптора среды приложение должно установить атрибуты среды, чтобы указать, какая версия вызовов функций ODBC будет использоваться. Для использования ODBC 3. *x* , вызовите функцию [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) с *атрибута* параметр значение SQL_ATTR_ODBC_VERSION и *ValuePtr* значение SQL_OV_ ODBC3.  
  
## <a name="see-also"></a>См. также  
 [Взаимодействие с SQL Server &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  