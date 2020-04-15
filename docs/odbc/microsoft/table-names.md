---
title: Названия таблиц (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 91a415cd456186f18ef358b9d504145f78152774
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303125"
---
# <a name="table-names"></a>Имена таблиц
При использовании драйвера dBASE, Microsoft Excel, Paradox или Text имена таблиц, которые встречаются в пункте FROM SELECT или DELETE, после положения INTO в INSERT, и после UPDATE, CREATE TABLE и DROP TABLE могут содержать действительный путь, основное имя и расширение названия файла.  
  
 Использование имени таблицы в другом месте в выписке S'L не поддерживает использование путей или расширений, но будет принимать только основное имя (например, EMP FROM C: ABC-EMP).  
  
 Можно использовать имена корреляций (псевдонимы). Пример:  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```
