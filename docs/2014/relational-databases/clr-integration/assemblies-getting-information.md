---
title: Получение сведений о сборках | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], metadata
- status information [SQL Server], assemblies
- metadata [SQL Server], assemblies
ms.assetid: 6aa7f18e-baad-4481-9777-8c3b230b392f
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e9940c597e176542fbfcbd7968ce96b496651f88
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087144"
---
# <a name="getting-information-about-assemblies"></a>Получение сведений о сборках
  Чтобы получить метаданные о сборках можно использовать следующие представления каталога и функции.  
  
 **Для получения сведений об отдельных сборках**  
  
-   [ASSEMBLYPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/assemblyproperty-transact-sql)  
  
 **Для получения сведений обо всех сборках в базе данных**  
  
-   [sys.assemblies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assemblies-transact-sql)  
  
 **Для получения сведений о файлах сборки, включая двоичные файлы сборки, исходные файлы и файлы отладки**  
  
-   [sys.assembly_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-files-transact-sql)  
  
 **Для получения сведений о перекрестных ссылках между сборками**  
  
-   [sys.assembly_references &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-references-transact-sql)  
  
 **Получение сведений об определяемых пользователем типов**  
  
-   [sys.assembly_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-types-transact-sql)  
  
-   [sys.types (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-types-transact-sql)  
  
 **Для получения сведений о общий язык среды выполнения (CLR) хранимых процедурах, триггерах и функциях**  
  
-   [sys.assembly_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
 **Для получения сведений об объектах, не использующей среду CLR**  
  
-   [sys.sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
## <a name="see-also"></a>См. также  
 [Сборки &#40;компонент Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)   
 [Конструирование сборок](../../relational-databases/clr-integration/assemblies-designing.md)   
 [Реализация сборок](assemblies-implementing.md)  
  
  
