---
title: SQLForeignKeys | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 93ad12cef5bcf894fbcd6c27c6d44327758bccf0
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39561734"
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает каскадные обновления и удаления через механизм ограничения внешнего ключа. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение SQL_CASCADE для столбцов, имеющих признак UPDATE_RULE и DELETE_RULE, если параметр CASCADE задан в предложении ON UPDATE или ON DELETE ограничения FOREIGN KEY. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение SQL_NO_ACTION для столбцов, имеющих признак UPDATE_RULE и DELETE_RULE, если параметр NO ACTION задан в предложении ON UPDATE или ON DELETE ограничения FOREIGN KEY.  
  
 Если в любом параметре функции **SQLForeignKeys** имеются недопустимые значения, функция **SQLForeignKeys** возвращает значение SQL_SUCCESS. Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 Функцию**SQLForeignKeys** можно выполнять в статическом серверном курсоре. При попытке выполнить функцию **SQLForeignKeys** для обновляемого курсора (динамического или набора ключей) будет возвращено значение SQL_SUCCESS_WITH_INFO, которое указывает на то, что тип курсора был изменен.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает выдачу сведений о таблицах, находящихся на связанных серверах, принимая двухкомпонентное имя в параметрах *FKCatalogName* и *PKCatalogName* : *Имя_Связанного_Сервера.Имя_Каталога*.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLForeignKeys](http://go.microsoft.com/fwlink/?LinkId=59344)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
