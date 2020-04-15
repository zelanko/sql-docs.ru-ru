---
title: Команда DELETE TAG Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE TAG command [ODBC]
ms.assetid: 4f4e1362-a5f3-4b15-8a3c-d4e96605f221
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 97ca5abca7e70f5dffdae9bf14ce64429fd203d5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303545"
---
# <a name="delete-tag-command"></a>Команда DELETE TAG
Удаляет теги или теги из файла соединения индекса (.cdx).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DELETE TAG TagName1 [OF CDXFileName1]  
   [, TagName2 [OF CDXFileName2]] ...  
  Or   
DELETE TAG ALL [OF CDXFileName]  
```  
  
## <a name="arguments"></a>Аргументы  
 *TagName1* *CDXFileName1* *(TagName2)*(OF *CDXFileName2)*...  
 Устраняет тег для удаления из файла соединения индекса. Вы можете удалить несколько тегов с одним DELETE TAG, включив список имен тегов, разделенных запятыми. Если в файлах открытого индекса есть два или более тегов с одинаковым названием, можно удалить тег из определенного файла индекса, включив *CDXFileName.*  
  
 ВСЕ *(КДКСFileName)*  
 Удаляет каждый тег из файла индекса соединения. Если текущая таблица имеет файл индекса структурного соединения, все теги удаляются из файла индекса, файл индекса удаляется с диска, а флаг в заголовке таблицы, указывающий на наличие связанного файла индекса структурного соединения, удаляется. Используйте ВСЕ с *CDXFileName,* чтобы удалить все теги из открытого файла индекса соединения, кроме файла индекса структурного соединения.  
  
## <a name="remarks"></a>Remarks  
 Файлы индекса соединения, созданные с помощью INDEX, содержат теги, соответствующие записям индекса. DELETE TAG используется для удаления тега или тегов из открытых файлов индекса соединения. Можно удалить только теги из сложных индексных файлов, открытых в текущей рабочей области. При удалении всех тегов из файла индекса соединения файл удаляется с диска.  
  
 Visual FoxPro сначала ищет тег в файле индекса структурного соединения (если он открыт). Если тега нет в файле индекса структурного соединения, Visual FoxPro ищет тег в других открытых файлах индекса соединения.  
  
## <a name="see-also"></a>См. также:  
 [Команда INDEX](../../odbc/microsoft/index-command.md)
