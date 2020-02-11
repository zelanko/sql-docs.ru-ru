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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5dd8de055521f4a1831d20a9a34bedb9309d1de6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67939785"
---
# <a name="table-names"></a>Имена таблиц
При использовании драйвера dBASE, Microsoft Excel, Paradox или Text имена таблиц, которые встречаются в предложении FROM инструкции SELECT или DELETE, после предложения INTO в инструкциях INSERT, а также после инструкции UPDATE, CREATE TABLE и DROP TABLE могут содержать допустимые путь, первичное имя и расширение имени файла. .  
  
 Использование имени таблицы в любом расположении в инструкции SQL не поддерживает использование путей или расширений, но принимает только основное имя (например, EMP из К:\АБК\ЕМП).  
  
 Можно использовать корреляционные имена (псевдонимы). Пример:  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```
