---
title: Удаление SQL Server индекса | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c2481c516714acd58ba243c614534b1079be6b0f
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73761575"
---
# <a name="dropping-a-sql-server-index"></a>Удаление индекса SQL Server

  Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB предоставляет функцию **IIndexDefinition::D ропиндекс** . Это позволяет потребителям удалять индексы из таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB предоставляет некоторые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ограничения ПЕРВИЧного ключа и УНИКАЛЬности в качестве индексов. Владелец таблицы, владелец базы данных и члены некоторых административных ролей могут изменять таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], удаляя ограничения. По умолчанию только владелец таблицы может удалять существующие индексы. Таким образом, будет ли функция **DropIndex** выполнена успешно или с ошибкой, зависит не только от прав доступа пользователя приложения, но также и от указанного типа индекса.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pTableID*. Элемент *eKind* параметра *pTableID* должен быть равен DBKIND_NAME.  
  
 Потребитель задает имя индекса в виде строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pIndexID*. Элемент *eKind* параметра *pIndexID* должен быть равен DBKIND_NAME. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB не поддерживает функцию OLE DB удаления всех индексов в таблице, если *pIndexID* имеет значение null. Если значение параметра *pIndexID* равно NULL, то возвращается E_INVALIDARG.  
  
## <a name="see-also"></a>См. также статью  
 [Таблицы и индексы](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX (Transact-SQL)](../../t-sql/statements/drop-index-transact-sql.md)  
  
  
