---
title: MSSQLSERVER_107 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 107 (Database Engine error)
ms.assetid: f33f514c-56aa-42e2-841b-e91244da90e2
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 4fee44ea6826f93ee32b8d22eb5cba00595627bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190448"
---
# <a name="mssqlserver107"></a>MSSQLSERVER_107
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|107|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|P_NOCORRMATCH|  
|Текст сообщения|Префикс столбца «%.*ls» не совпадает с именем таблицы или псевдонимом, используемым в запросе.|  
  
## <a name="explanation"></a>Объяснение  
 Список выбора запроса содержит звездочку (*), которая неправильно дополнена префиксом столбца. Эта ошибка может быть возвращена при следующих условиях.  
  
-   Префикс столбца не соответствует ни одному имени таблицы или псевдониму, используемому в запросе. Например, в следующей инструкции в качестве префикса столбца используется псевдоним (`T1`), но этот псевдоним не определен в предложении FROM.  
  
    ```  
    SELECT T1.* FROM dbo.ErrorLog;  
    ```  
  
-   В качестве префикса столбца указано имя таблицы, а в предложении FROM для таблицы указан псевдоним. Например, в следующей инструкции в качестве префикса столбца используется имя таблицы `ErrorLog`, но таблица имеет псевдоним (`T1`), определенный в предложении FROM.  
  
    ```  
    SELECT ErrorLog.* FROM dbo.ErrorLog AS T1;  
    ```  
  
     Если в предложении FROM предусмотрен псевдоним для имени таблицы, то для обозначения префиксом столбцов этой таблицы можно использовать только псевдоним.  
  
## <a name="user-action"></a>Действие пользователя  
 Префиксы столбцов должны быть согласованы с именами таблиц или псевдонимами, указанными в предложении FROM запроса. Например, приведенные выше инструкции могут быть исправлены следующим образом:  
  
```  
SELECT T1.* FROM dbo.ErrorLog AS T1;  
```  
  
 или диспетчер конфигурации служб  
  
```  
SELECT ErrorLog.* FROM dbo.ErrorLog;  
```  
  
## <a name="see-also"></a>См. также  
 [MSSQLSERVER_4104](mssqlserver-4104-database-engine-error.md)  
  
  