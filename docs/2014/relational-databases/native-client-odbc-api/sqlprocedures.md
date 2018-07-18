---
title: SQLProcedures | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a7855016bf7c0dec86775cc6a1a289d0b317031
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417723"
---
# <a name="sqlprocedures"></a>SQLProcedures
  Все хранимые процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращают какое-либо значение. **SQLProcedures** сообщает значение SQL_PT_FUNCTION столбцу результирующего набора PROCEDURE_TYPE.  
  
 **SQLProcedures** возвращает SQL_SUCCESS независимо от наличия значения существуют для *CatalogName, SchemaName* или *ProcName* параметров. Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 **SQLProcedures** может быть выполнена для статического серверного курсора. При попытке выполнить **SQLProcedures** для обновляемого (динамического или набора ключей) курсора будет возвращено значение SQL_SUCCESS_WITH_INFO, что тип курсора был изменен.  
  
 **SQLProcedures** возвращает сведения обо всех процедурах, имена которых соответствуют *ProcName* и могут быть выполнены текущим пользователем, или для которого текущий пользователь имеет разрешение VIEW DEFINITION.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLProcedures](http://go.microsoft.com/fwlink/?LinkId=59364)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
