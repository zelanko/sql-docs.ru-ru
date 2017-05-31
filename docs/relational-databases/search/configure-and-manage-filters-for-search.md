---
title: "Настройка поисковых фильтров и управление ими | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-search
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full-text search [SQL Server], filters
- filters [full-text search]
ms.assetid: 7ccf2ee0-9854-4253-8cca-1faed43b7095
caps.latest.revision: 68
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a9a3c108e0a9c66daa6a6cde799694ac8491e796
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="configure-and-manage-filters-for-search"></a>Настройка поисковых фильтров и управление ими
  Индексирование документа в столбце типов данных **varbinary**, **varbinary(max)**, **image**или **xml** требует дополнительной обработки. Такая обработка должна выполняться фильтром. Фильтр извлекает из документа текстовые данные (устранение форматирования). Затем фильтр отправляет текст в компонент средства разбиения по словам для языка, связанного со столбцом таблицы.  
  
 Данный фильтр зависит от типа данных документа (DOC, PDF, XLS, XML и т. д.). Такие фильтры реализуют интерфейс IFilter. Для получения дополнительных сведений об этих типах документов выполните запрос к представлению каталога [sys.fulltext_document_types](../../relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql.md) .  
  
 Двоичные документы можно хранить в одном столбце **varbinary(max)** или **image** . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выбирает для каждого документа правильный фильтр в соответствии с расширением файла. Поскольку при сохранении файла в столбце типа **varbinary(max)** или **image** его расширение не отображается, расширение файла (DOC, DOCX, PDF и т. д.) нужно хранить в отдельном столбце таблицы, который называется столбцом типов. Столбец типов может иметь любой символьный тип данных и содержит расширение файла документа (например, DOC в случае документа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word). В таблице **Document** базы данных [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]столбец **Document** имеет тип **varbinary(max)**, а столбец **FileExtension**— тип **nvarchar(8)**.  
  
> [!NOTE]  
>  Фильтр может быть способен обрабатывать объекты, внедренные в родительский объект, в зависимости от его реализации. Однако в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] фильтры не настроены на переход по ссылкам на другие объекты.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливаются собственные фильтры XML и HTML. Кроме того, любые фильтры для собственных форматов [!INCLUDE[msCoName](../../includes/msconame-md.md)] (DOC, XDOC, PPT и т. д.), которые уже установлены в операционной системе, также загружаются средствами  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы определить, какие фильтры загружены в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в данный момент, используйте хранимую процедуру [sp_help_fulltext_system_components](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md) следующим образом:  
  
```  
EXEC sp_help_fulltext_system_components 'filter';   
```  
  
 Прежде чем использовать фильтры для форматов, не принадлежащих [!INCLUDE[msCoName](../../includes/msconame-md.md)] , их необходимо вручную загрузить на экземпляр сервера. Сведения об установке дополнительных фильтров см. в статье [Просмотр или изменение зарегистрированных фильтров и разделителей слов](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md).  
  
 **Просмотр столбца типов в существующем полнотекстовом индексе**  
  
-   [sys.fulltext_index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [sys.fulltext_index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)   
 [Совместимость FILESTREAM с другими компонентами SQL Server](../../relational-databases/blob/filestream-compatibility-with-other-sql-server-features.md)  
  
  
