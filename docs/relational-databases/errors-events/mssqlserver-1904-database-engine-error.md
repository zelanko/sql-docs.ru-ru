---
title: MSSQLSERVER_1904 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1904 (Database Engine error)
ms.assetid: 2a35d57d-74e2-45a2-8f67-3f2e51d69712
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ea12450aba44938a1333687d14aa0dc5dfc471e4
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67896834"
---
# <a name="mssqlserver_1904"></a>MSSQLSERVER_1904
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1904|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|KEYCOUNT|  
|Текст сообщения|Сообщение %S_MSG "%.*ls", касающееся таблицы "%.\*ls", содержит %d имен столбцов в списке ключей %S_MSG. Максимальный предел для индекса или списка ключевых столбцов статистики равен %d.|  
  
## <a name="explanation"></a>Объяснение  
Список ключевых столбцов для указанного индекса или статистики данных превышает максимально допустимое количество столбцов.  
  
## <a name="user-action"></a>Действие пользователя  
Измените список ключевых столбцов, чтобы он включал не больше указанного максимального количества столбцов.  
  
Применительно к некластеризованным индексам рассмотрите возможность использования предложения INCLUDE в инструкции CREATE INDEX для добавления столбцов к индексу в качестве неключевых столбцов. Этот метод позволяет предотвратить превышение текущего ограничения на размер индекса, которое составляет максимум 16 ключевых столбцов. Дополнительные сведения см. в статье [Create Indexes with Included Columns](~/relational-databases/indexes/create-indexes-with-included-columns.md).  
  
## <a name="see-also"></a>См. также:  
[CREATE INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/create-index-transact-sql.md)  
[CREATE STATISTICS (Transact-SQL)](~/t-sql/statements/create-statistics-transact-sql.md)  
  
