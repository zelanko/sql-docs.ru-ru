---
title: Удаление индекса SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9be4e3607097c476f083c32eed9f13fecc0d3842
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704525"
---
# <a name="dropping-a-sql-server-index"></a>Удаление индекса SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DBа собственного клиента предоставляет функцию **IIndexDefinition::D ропиндекс** . Это позволяет потребителям удалять индексы из таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента предоставляет некоторые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ограничения первичного ключа и уникальности в качестве индексов. Владелец таблицы, владелец базы данных и члены некоторых административных ролей могут изменять таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], удаляя ограничения. По умолчанию только владелец таблицы может удалять существующие индексы. Таким образом, будет ли функция **DropIndex** выполнена успешно или с ошибкой, зависит не только от прав доступа пользователя приложения, но также и от указанного типа индекса.  
  
 Пользователь задает имя таблицы в виде символьной строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pTableID*. Элемент *eKind* параметра *pTableID* должен быть равен DBKIND_NAME.  
  
 Потребитель задает имя индекса в виде строки в Юникоде в элементе *pwszName* объединения *uName* в параметре *pIndexID*. Элемент *eKind* параметра *pIndexID* должен быть равен DBKIND_NAME. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента не поддерживает функцию OLE DB удаления всех индексов в таблице, если *pIndexID* имеет значение null. Если значение параметра *pIndexID* равно NULL, то возвращается E_INVALIDARG.  
  
## <a name="see-also"></a>См. также  
 [Таблицы и индексы](tables-and-indexes.md)   
 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)   
 [DROP INDEX (Transact-SQL)](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
