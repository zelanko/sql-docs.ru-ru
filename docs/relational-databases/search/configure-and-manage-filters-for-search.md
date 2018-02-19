---
title: "Настройка поисковых фильтров и управление ими | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: search
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-search
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full-text search [SQL Server], filters
- filters [full-text search]
ms.assetid: 7ccf2ee0-9854-4253-8cca-1faed43b7095
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4c3a5a90c6dffb76f4569d86615cbb0034f3db5
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="configure-and-manage-filters-for-search"></a>Настройка поисковых фильтров и управление ими
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Индексирование документа в столбце с типом данных **varbinary**, **varbinary(max)**, **image** или **xml** требует дополнительной обработки. Такая обработка должна выполняться фильтром. Фильтр извлекает из документа текстовые данные (устранение форматирования). Затем фильтр отправляет текст в компонент средства разбиения по словам для языка, связанного со столбцом таблицы.  
  
 Данный фильтр зависит от типа данных документа (DOC, PDF, XLS, XML и т. д.). Такие фильтры реализуют интерфейс IFilter. Для получения дополнительных сведений об этих типах документов выполните запрос к представлению каталога [sys.fulltext_document_types](../../relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql.md) .  
  
 Двоичные документы можно хранить в одном столбце **varbinary(max)** или **image** . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выбирает для каждого документа правильный фильтр в соответствии с расширением файла. Поскольку при сохранении файла в столбце типа **varbinary(max)** или **image** его расширение не отображается, расширение файла (DOC, DOCX, PDF и т. д.) нужно хранить в отдельном столбце таблицы, который называется столбцом типов. Столбец типов может иметь любой символьный тип данных и содержит расширение файла документа (например, DOC в случае документа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word). В таблице **Document** базы данных [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]столбец **Document** имеет тип **varbinary(max)**, а столбец **FileExtension**— тип **nvarchar(8)**.  
  
> [!NOTE]  
>  Фильтр может быть способен обрабатывать объекты, внедренные в родительский объект, в зависимости от его реализации. Однако в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] фильтры не настроены на переход по ссылкам на другие объекты.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливаются собственные фильтры XML и HTML. Кроме того, любые фильтры для собственных форматов [!INCLUDE[msCoName](../../includes/msconame-md.md)] (DOC, XDOC, PPT и т. д.), которые уже установлены в операционной системе, также загружаются средствами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы определить, какие фильтры загружены в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в данный момент, используйте хранимую процедуру [sp_help_fulltext_system_components](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md) следующим образом:  
  
```  
EXEC sp_help_fulltext_system_components 'filter';   
```  
  
 Прежде чем использовать фильтры для форматов, не принадлежащих [!INCLUDE[msCoName](../../includes/msconame-md.md)] , их необходимо вручную загрузить на экземпляр сервера. Сведения об установке дополнительных фильтров см. в статье [Просмотр или изменение зарегистрированных фильтров и разделителей слов](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md).  
  
 **Просмотр столбца типов в существующем полнотекстовом индексе**  
  
-   [sys.fulltext_index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [sys.fulltext_index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)   
 [Совместимость FILESTREAM с другими компонентами SQL Server](../../relational-databases/blob/filestream-compatibility-with-other-sql-server-features.md)  
  
  
