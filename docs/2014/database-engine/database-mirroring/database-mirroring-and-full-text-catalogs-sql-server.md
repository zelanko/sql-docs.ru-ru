---
title: Зеркальное отображение баз данных и полнотекстовые каталоги (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- full-text catalogs [SQL Server], database mirroring
- catalogs [SQL Server], database mirroring
ms.assetid: e34072ae-fe8a-462d-bb03-02fa0987f793
caps.latest.revision: 49
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d0807ba4c0d8a23d15be4dab7745f5abbebd3aea
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101812"
---
# <a name="database-mirroring-and-full-text-catalogs-sql-server"></a>Зеркальное отображение баз данных и полнотекстовые каталоги (SQL Server)
  Чтобы создать зеркало базы данных с полнотекстовым каталогом, воспользуйтесь, как обычно, резервным копированием и восстановлением, чтобы создать полную резервную копию основной базы данных, и скопируйте ее на зеркальный сервер. Дополнительные сведения см. в разделе [Подготовка зеркальной базы данных к зеркальному отображению (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md).  
  
## <a name="full-text-catalog-and-indexes-before-failover"></a>Полнотекстовой каталог и индексы до отработки отказа  
 В новой зеркальной базе данных полнотекстовый каталог будет таким же, как и во время резервного копирования базы данных. После включения зеркального отображения базы данных, любые сделанные инструкциями DDL изменения на уровне каталогов (CREATE FULLTEXT CATALOG, ALTER FULLTEXT CATALOG, DROP FULLTEXT CATALOG) протоколируются, отправляются на зеркальный сервер и воспроизводятся в зеркальной базе данных. Однако изменения на уровне индексов не воспроизводятся в зеркальной базе данных, так как протоколирование этого на основном сервере не ведется. Таким образом, при изменении содержимого полнотекстового каталога основной базы содержимое полнотекстового каталога зеркальной базы становится несинхронизированным.  
  
## <a name="full-text-indexes-after-failover"></a>Полнотекстовые индексы после отработки отказа  
 После отработки отказа полное сканирование полнотекстового индекса нового основного сервера может быть необходимо или полезно в следующих ситуациях.  
  
-   Если выключено слежение за изменениями в полнотекстовом индексе, необходимо запустить полное сканирование индекса при помощи следующей инструкции:  
  
     ALTER FULLTEXT INDEX ON *имя_таблицы* START FULL POPULATION  
  
-   Если полнотекстовой индекс настроен для автоматического отслеживания изменений, то происходит автоматическая синхронизация полнотекстового индекса. Однако синхронизация замедляет полнотекстовую производительность. Если производительность становится слишком низкой, можно запустить полное сканирование путем отключения отслеживания изменений, а затем снова установить отслеживание изменений в автоматический режим:  
  
    -   Отключение отслеживания изменений:  
  
         ALTER FULLTEXT INDEX ON *имя_таблицы* SET CHANGE_TRACKING OFF  
  
    -   Переключение автоматического отслеживания изменений в автоматический режим:  
  
         ALTER FULLTEXT INDEX ON *имя_таблицы* SET CHANGE_TRACKING AUTO  
  
    > [!NOTE]  
    >  Чтобы проверить, включено ли автоматическое отслеживание изменений, можно воспользоваться функцией [OBJECTPROPERTYEX](/sql/t-sql/functions/objectproperty-transact-sql) для запроса свойства **TableFullTextBackgroundUpdateIndexOn** таблицы.  
  
 Дополнительные сведения см. в статье [ALTER FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-index-transact-sql).  
  
> [!NOTE]  
>  Запуск сканирования после отработки отказа работает так же, как и после восстановления.  
  
## <a name="after-forcing-service"></a>После принудительного запуска службы  
 После того, как обслуживание принудительно переключилось на зеркальный сервер (с возможностью потери данных), запустите полное сканирование. Используемый для запуска полного сканирования метод зависит от слежения за изменениями полнотекстового индекса. Дополнительные сведения см. в подразделе «Полнотекстовые индексы после отработки отказа» ранее в этом разделе.  
  
## <a name="see-also"></a>См. также  
 [ALTER FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-index-transact-sql)   
 [CREATE FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [DROP FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/drop-fulltext-index-transact-sql)   
 [Зеркальное отображение базы данных (SQL Server)](database-mirroring-sql-server.md)   
 [Создание резервных копий и восстановление полнотекстовых каталогов и индексов](../../relational-databases/indexes/indexes.md)  
  
  
