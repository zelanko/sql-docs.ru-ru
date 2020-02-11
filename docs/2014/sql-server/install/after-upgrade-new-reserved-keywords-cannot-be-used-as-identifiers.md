---
title: После обновления новые зарезервированные ключевые слова нельзя использовать в качестве идентификаторов | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- keywords [SQL Server], after upgrade
- keywords [SQL Server], reserved
- keywords [SQL Server]
ms.assetid: cb242081-54f8-4273-a8ef-52f3751c25ef
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d187fbe95a75091b0cbcf4bf09225c5f60a9af01
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66096890"
---
# <a name="after-upgrade-new-reserved-keywords-cannot-be-used-as-identifiers"></a>После обновления новые зарезервированные ключевые слова не могут быть использованы в качестве идентификаторов
  Советник по переходу обнаружил использование слов, зарезервированных в качестве ключевых. Зарезервированное ключевое слово нельзя использовать в качестве идентификатора или имени объекта, если только имя не заключено в разделители.  
  
## <a name="component"></a>Компонент  
 Компонент Database Engine  
  
## <a name="description"></a>Description  
 Для уровня совместимости 90 и ниже следующие слова не являются зарезервированными и могут использоваться в качестве идентификаторов и имен объектов в скриптах [!INCLUDE[tsql](../../includes/tsql-md.md)]. Для уровня совместимости 100 эти слова являются зарезервированными ключевыми словами и не должны использоваться в качестве идентификаторов и имен объектов.  
  
-   EXTERNAL  
  
-   MERGE  
  
-   PIVOT  
  
-   REVERT  
  
-   STOPLIST  
  
-   TABLESAMPLE  
  
-   UNPIVOT  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Рекомендуется переименовать объект. Если это не удается сделать до обновления, то попробуйте воспользоваться следующими методами для переименования объекта.  
  
-   Сохраните уровень совместимости 90 или ниже.  
  
-   Для ссылок на объект пользуйтесь идентификаторами с разделителями. Например, оператор `CREATE TABLE [MERGE] ([MERGE] int);` использует квадратные скобки для разделения имени объекта при слиянии.  
  
## <a name="external-resources"></a>Внешние ресурсы  
 [Зарезервированные ключевые слова &#40;&#41;Transact-SQL](/sql/t-sql/language-elements/reserved-keywords-transact-sql)  
  
 [&#41;Transact-SQL &#40;MERGE](/sql/t-sql/statements/merge-transact-sql)  
  
 [Идентификаторы с разделителями (компонент Database Engine)](https://go.microsoft.com/fwlink/?LinkId=112509)  
  
 [Уровень совместимости ALTER DATABASE &#40;&#41;Transact-SQL](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
