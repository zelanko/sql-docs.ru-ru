---
title: Настройка поисковых фильтров и управление ими | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], filters
- filters [full-text search]
ms.assetid: 7ccf2ee0-9854-4253-8cca-1faed43b7095
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e9a57c95226a9b277cfb718b40b5d0525b1f8eb3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "84997748"
---
# <a name="configure-and-manage-filters-for-search"></a>Настройка поисковых фильтров и управление ими
  Индексирование документа в столбце типов данных `varbinary`, `varbinary(max)`, `image` или `xml` требует дополнительной обработки. Такая обработка должна выполняться фильтром. Фильтр извлекает из документа текстовые данные (устранение форматирования). Затем фильтр отправляет текст в компонент средства разбиения по словам для языка, связанного со столбцом таблицы.  
  
 Данный фильтр зависит от типа данных документа (DOC, PDF, XLS, XML и т. д.). Такие фильтры реализуют интерфейс IFilter. Для получения дополнительных сведений об этих типах документов выполните запрос к представлению каталога [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) .  
  
 Двоичные документы можно хранить в одном столбце `varbinary(max)` или `image`. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выбирает для каждого документа правильный фильтр в соответствии с расширением файла. Поскольку расширение файла не отображается, если файл хранится в `varbinary(max)` `image` столбце или, расширение файла (doc, XLS, PDF и т. д.) должно храниться в отдельном столбце таблицы, называемом столбцом типа. Столбец типов может иметь любой символьный тип данных и содержит расширение файла документа (например, DOC в случае документа [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Word). В таблице **документа** в [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] столбец **документа** имеет тип `varbinary(max)` , а столбец Type, **fileExtension**, имеет тип `nvarchar(8)` .  
  
> [!NOTE]  
>  Фильтр может быть способен обрабатывать объекты, внедренные в родительский объект, в зависимости от его реализации. Однако в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] фильтры не настроены на переход по ссылкам на другие объекты.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливаются собственные фильтры XML и HTML. Кроме того, любые фильтры для собственных форматов [!INCLUDE[msCoName](../../../includes/msconame-md.md)] (DOC, XDOC, PPT и т. д.), которые уже установлены в операционной системе, также загружаются средствами  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Чтобы определить, какие фильтры загружены в экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]в данный момент, используйте хранимую процедуру [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) следующим образом:  
  
```  
EXEC sp_help_fulltext_system_components 'filter';   
```  
  
 Прежде чем использовать фильтры для форматов, не принадлежащих [!INCLUDE[msCoName](../../../includes/msconame-md.md)] , их необходимо вручную загрузить на экземпляр сервера. Сведения об установке дополнительных фильтров см. в статье [Просмотр или изменение зарегистрированных фильтров и разделителей слов](view-or-change-registered-filters-and-word-breakers.md).  
  
 **Просмотр столбца типов в существующем полнотекстовом индексе**  
  
-   [sys.fulltext_index_columns (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
## <a name="see-also"></a>См. также:  
 [sys. fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)   
 [Совместимость FILESTREAM с другими функциями SQL Server](../blob/filestream-compatibility-with-other-sql-server-features.md)  
  
  
