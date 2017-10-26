---
title: "Команда Удалить ТЕГ | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DELETE TAG command [ODBC]
ms.assetid: 4f4e1362-a5f3-4b15-8a3c-d4e96605f221
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c10f0daac2f672b40b3bda050401e9873afe6aa8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="delete-tag-command"></a>Удаление ТЕГА команды
Удаляет тег или теги из файла составной индекс (.cdx).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DELETE TAG TagName1 [OF CDXFileName1]  
   [, TagName2 [OF CDXFileName2]] ...  
  Or   
DELETE TAG ALL [OF CDXFileName]  
```  
  
## <a name="arguments"></a>Аргументы  
 *TagName1*OF *CDXFileName1*[, *TagName2*[OF *CDXFileName2*]]...  
 Указывает тег, чтобы удалить из файла составной индекс. Можно удалить несколько тегов с одной удалить ТЕГ, включая список тегов, разделенных точками с запятой. Если два или несколько тегов с тем же именем существует в файлах открыть индекс, можно удалить тег из файла конкретного индекса, включая OF *CDXFileName*.  
  
 ВСЕ [OF *CDXFileName*]  
 Удаляет каждый тег из файла составной индекс. Если текущая таблица содержит файл структурных составной индекс, из файла индекса удаляются все теги, файл индекса удаляется с диска и флаг в заголовке таблицы, что указывает на наличие структурных комплексной индексный файл удален. Использование в рамках OF *CDXFileName* для удаления всех тегов из файла открыть составной индекс, отличного от файла структурных составной индекс.  
  
## <a name="remarks"></a>Замечания  
 Составные файлы индекса, созданных с помощью ИНДЕКСА, содержат теги, соответствующий записи индекса. УДАЛИТЬ ТЕГ используется для удаления файлов открыть составной индекс тег или теги. Можно удалить только теги из составного индекса файлы, открытые в текущей рабочей области. Если удалить все теги из файла составной индекс, файл удаляется с диска.  
  
 Visual FoxPro находит первый тег в файле структурных составной индекс (если он открыт). Если тег не в файле структурных составной индекс, Visual FoxPro ищет тег в других файлах открыть составной индекс.  
  
## <a name="see-also"></a>См. также:  
 [ИНДЕКС команды](../../odbc/microsoft/index-command.md)

