---
title: Настройка поисковых фильтров и управление ими | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], filters
- filters [full-text search]
ms.assetid: 7ccf2ee0-9854-4253-8cca-1faed43b7095
caps.latest.revision: 68
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7b19f9141df65be952551dbb899b6cb30544e9a3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278930"
---
# <a name="configure-and-manage-filters-for-search"></a>Настройка поисковых фильтров и управление ими
  Индексирование документа в `varbinary`, `varbinary(max)`, `image`, или `xml` столбце с типом данных требует дополнительной обработки. Такая обработка должна выполняться фильтром. Фильтр извлекает из документа текстовые данные (устранение форматирования). Затем фильтр отправляет текст в компонент средства разбиения по словам для языка, связанного со столбцом таблицы.  
  
 Данный фильтр зависит от типа данных документа (DOC, PDF, XLS, XML и т. д.). Такие фильтры реализуют интерфейс IFilter. Для получения дополнительных сведений об этих типах документов выполните запрос к представлению каталога [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) .  
  
 Двоичные документы можно хранить в одном столбце `varbinary(max)` или `image`. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выбирает для каждого документа правильный фильтр в соответствии с расширением файла. Поскольку расширение файла не отображается при сохранении файла в `varbinary(max)` или `image` столбца, расширение файла (doc, XLS, .pdf и т. д.) должны храниться в отдельном столбце таблицы, который называется столбцом типов. Столбец типов может иметь любой символьный тип данных и содержит расширение файла документа (например, DOC в случае документа [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Word). В **документа** в таблицу [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], **документа** столбец имеет тип `varbinary(max)`, а столбец, **FileExtension**, имеет тип `nvarchar(8)`.  
  
> [!NOTE]  
>  Фильтр может быть способен обрабатывать объекты, внедренные в родительский объект, в зависимости от его реализации. Однако в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] фильтры не настроены на переход по ссылкам на другие объекты.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливаются собственные фильтры XML и HTML. Кроме того, любые фильтры для собственных форматов [!INCLUDE[msCoName](../../../includes/msconame-md.md)] (DOC, XDOC, PPT и т. д.), которые уже установлены в операционной системе, также загружаются средствами  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Чтобы определить, какие фильтры загружены в экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]в данный момент, используйте хранимую процедуру [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) следующим образом:  
  
```  
EXEC sp_help_fulltext_system_components 'filter';   
```  
  
 Прежде чем использовать фильтры для форматов, не принадлежащих [!INCLUDE[msCoName](../../../includes/msconame-md.md)] , их необходимо вручную загрузить на экземпляр сервера. Сведения об установке дополнительных фильтров см. в статье [Просмотр или изменение зарегистрированных фильтров и разделителей слов](view-or-change-registered-filters-and-word-breakers.md).  
  
 **Просмотр столбца типов в существующем полнотекстовом индексе**  
  
-   [sys.fulltext_index_columns (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
## <a name="see-also"></a>См. также  
 [sys.fulltext_index_columns (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)   
 [Совместимость FILESTREAM с другими компонентами SQL Server](../blob/filestream-compatibility-with-other-sql-server-features.md)  
  
  
