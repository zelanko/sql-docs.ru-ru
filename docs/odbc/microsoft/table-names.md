---
title: Имена таблиц | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303125"
---
# <a name="table-names"></a>Имена таблиц
При использовании драйвера dBASE, Microsoft Excel, Paradox или Text имена таблиц, которые встречаются в предложении FROM инструкции SELECT или DELETE, после предложения INTO в инструкциях INSERT, а также после инструкции UPDATE, CREATE TABLE и DROP TABLE могут содержать допустимые путь, первичное имя и расширение имени файла.  
  
 Использование имени таблицы в любом расположении в инструкции SQL не поддерживает использование путей или расширений, но принимает только основное имя (например, EMP из К:\АБК\ЕМП).  
  
 Можно использовать корреляционные имена (псевдонимы). Пример:  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```
